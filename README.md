# IoT-Experiments-

**🔌 IoT Basics with Arduino & ESP8266**
This repository contains beginner-friendly IoT projects using Arduino, ESP8266, and various sensors. These projects cover basic IoT principles, sensor integration, and WiFi-based control.

**🛠 Arduino IDE Installation & Online Alternatives**

1️⃣ Install Arduino IDE (Offline)
🔹 For Windows:
Download from Arduino Official Site.
Run the installer and follow the setup.
Install USB drivers if prompted.

🔹 For macOS & Linux:
Download the Mac/Linux version from Arduino Official Site.
Extract and install the software.

2️⃣ Online Alternatives (No Installation Needed)
🚀 If you don’t want to install Arduino IDE, use these online platforms:

✅ Arduino Web Editor (Official & cloud-based)

✅ TinkerCAD Circuits (Simulate circuits & write code)

✅ Wokwi Simulator (Advanced simulation for Arduino, ESP32, etc.)

These platforms allow you to write, test, and simulate Arduino code online!

**📌 Projects Included**
**1️⃣ Blinking LED (Basic Setup)**
Simple LED blink using Arduino Uno.
Components: Arduino, LED, 220Ω Resistor.
Code Here:
void setup() {

  pinMode(13, OUTPUT);
}

void loop() {
  digitalWrite(13, HIGH);  // Turn LED ON
  delay(1000);             // Wait 1 sec
  digitalWrite(13, LOW);   // Turn LED OFF
  delay(1000);             // Wait 1 sec
}


**2️⃣ Temperature & Humidity Sensor (DHT11)**
Components:
Arduino Uno
LED
220Ω resistor
Jumper wires
Circuit Connection:
LED +ve (Anode) → Arduino Pin 13
LED -ve (Cathode) → GND via 220Ω resistor
Code Here:
#include <DHT.h>

#define DHTPIN 2      
#define DHTTYPE DHT11 

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  float temp = dht.readTemperature();
  Serial.print("Temperature: ");
  Serial.print(temp);
  Serial.println("°C");
  delay(2000);
}


**3️⃣ Motion Detection using PIR Sensor**
Components:
Arduino Uno
DHT11 Temperature & Humidity Sensor
10kΩ Resistor
Jumper Wires
Circuit Connection:
DHT11 VCC → 5V
DHT11 GND → GND
DHT11 Data Pin → Pin 2
Code Here:
int pirPin = 2;
int ledPin = 13;

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  int motion = digitalRead(pirPin);
  if (motion == HIGH) {
    digitalWrite(ledPin, HIGH);  // Turn LED ON if motion detected
  } else {
    digitalWrite(ledPin, LOW);   // Turn LED OFF if no motion
  }
}


**4️⃣ IoT-Based LED Control using Blynk & ESP8266**
Components:
ESP8266 NodeMCU
LED
220Ω Resistor
Blynk App (for smartphone control)
Circuit Connection:
LED +ve → D2 (GPIO4)
LED -ve → GND
Code Here:
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

char auth[] = "Your_Blynk_Auth_Token";
char ssid[] = "Your_WiFi_Name";
char pass[] = "Your_WiFi_Password";

void setup() {
  Blynk.begin(auth, ssid, pass);
  pinMode(4, OUTPUT);
}

void loop() {
  Blynk.run();
}



**🔧 Requirements**
Arduino IDE for coding and uploading sketches.
ESP8266/NodeMCU libraries for WiFi-based projects.
DHT11 & PIR Sensor libraries (install via Arduino Library Manager).
