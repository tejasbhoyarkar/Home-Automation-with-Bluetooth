# Home-Automation-with-Bluetooth
TASK 2 (EMBEDDED SYSTEMS INTERNSHIP)

COMPANY: CODTECH IT SOLUTIONS

NAME: TEJAS KAILASH BHOYARKAR

INTERN ID: CTO8NSD

DOMAIN: EMBEDDED SYSTEMS

BATCH DURATION: January 20th,2025 to February 20th,2025 (4 Weeks)

MENTOR NAME: Neela Santhosh Kumar TASK:-- Home Automation with Bluetooth with esp32 module to display current. Display of screen or physcial on or off the module 

Overview

GitHub plays a crucial role in managing and sharing code for Home Automation projects using an ESP32 with a Bluetooth module. It serves as a version control platform that helps developers collaborate, track changes, and document their work efficiently.

Hardware Requirements
ESP32 Microcontroller (e.g., ESP32 Dev Kit v1)
LM35 Temperature Sensor
Jumper Wires
Breadboard (optional)

Software Requirements
Arduino IDE (or PlatformIO) to program the ESP32.
ESP32 Board Package installed in Arduino IDE.
Installation

Clone the Repository
Clone this repository to your local machine:
https://github.com/tejasbhoyarkar/Home-Automation-with-Bluetooth/edit/main/README.md


Hardware Setup

Arduino IDE Setup

Open the Arduino IDE. Install the ESP32 board package: Go to File > Preferences. In the Additional Boards Manager URLs field, add the following URL:
 Go to Tools > Board > Board Manager, search for "ESP32", and install it.
Select the ESP32 board: Go to Tools > Board > ESP32 Dev Module (or the appropriate ESP32 variant). Select the correct COM port under Tools > Port.

COMPONENTS REQUIRED:--

ESP32 Development Board

10kΩ Resistor (optional for pull-down)

Connecting Wires

Breadboard

LED

Power Supply

Cricuit Diagram
![image](https://github.com/user-attachments/assets/054b94a4-a6d0-4b54-ab41-31cf346dba7e)

Installation & Setup

Upload the Code to ESP32

Connect your microcontroller to your PC.

Open the Arduino IDE.

Install the required libraries (if needed).

Upload the following code:

include "BluetoothSerial.h"

#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED) #error Bluetooth is not enabled! Please run make menuconfig to and enable it #endif

BluetoothSerial SerialBT; int received;// received value will be stored in this variable char receivedChar;// received value will be stored as CHAR in this variable

const char turnON ='a'; const char turnOFF ='b'; const int LEDpin = 23;

void setup() { Serial.begin(115200); SerialBT.begin("ESP32_Robojax"); //Bluetooth device name Serial.println("The device started, now you can pair it with bluetooth!"); Serial.println("To turn ON send: a");//print on serial monitor
Serial.println("To turn OFF send: b"); //print on serial monitor pinMode(LEDpin, OUTPUT);

}

void loop() { receivedChar =(char)SerialBT.read();

if (Serial.available()) { SerialBT.write(Serial.read());

} if (SerialBT.available()) {

SerialBT.print("Received:");// write on BT app
SerialBT.println(receivedChar);// write on BT app      
Serial.print ("Received:");//print on serial monitor
Serial.println(receivedChar);//print on serial monitor    
//SerialBT.println(receivedChar);//print on the app    
//SerialBT.write(receivedChar); //print on serial monitor
if(receivedChar == turnON)
{
 SerialBT.println("LED ON:");// write on BT app
 Serial.println("LED ON:");//write on serial monitor
 digitalWrite(LEDpin, HIGH);// turn the LED ON
   
}
if(receivedChar == turnOFF)
{
 SerialBT.println("LED OFF:");// write on BT app
 Serial.println("LED OFF:");//write on serial monitor
  digitalWrite(LEDpin, LOW);// turn the LED off 
}    
} delay(20); }

Connect via Serial Bluetooth Terminal App

Install Serial Bluetooth Terminal from the Play Store.

Pair your Bluetooth module with your phone.

Open the app, connect to your module, and send:

"a" → Turns the LED ON

"b" → Turns the LED OFF

WORKING:--

This project allows users to control an LED wirelessly using Bluetooth communication between an ESP32 microcontroller and a mobile phone running the Serial Bluetooth Terminal app.

Step-by-Step Working

Bluetooth Communication Setup
The ESP32 has a built-in Bluetooth module, which allows wireless communication with the Serial Bluetooth Terminal app on a smartphone.

The mobile app sends ASCII characters ('a' and 'b') via Bluetooth Serial (UART), which the ESP32 reads and processes.

Command Processing in ESP32
The ESP32 continuously listens for incoming Bluetooth data.

When the user sends a command from the Serial Bluetooth Terminal app, the ESP32 reads the received character and performs an action accordingly:

'a' → Turn LED ON

'b' → Turn LED OFF

LED Control
If ESP32 receives 'a', it sets the LED pin to HIGH, turning it ON.

If ESP32 receives 'b', it sets the LED pin to LOW, turning it OFF.

Serial Monitor Logging
ESP32 prints debug messages ("LED ON" or "LED OFF") to the Serial Monitor for real-time feedback.

This helps in verifying whether the Bluetooth commands are received correctly.

Mobile App Interaction
The user interacts with the system via the Serial Bluetooth Terminal app:

Pair the ESP32 Bluetooth with the smartphone.

Open the Serial Bluetooth Terminal app and connect to ESP32.

Send 'a' to turn the LED ON and 'b' to turn it OFF.

How to Run the Project-->

Open the .ino file in Arduino IDE.

Connect your ESP32 board and select the correct COM Port.

Upload the code to the ESP32.

Open Serial Monitor (Baud rate: 115200).










