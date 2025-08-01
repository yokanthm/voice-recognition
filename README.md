🗣️ Arduino Voice Command Based LED Control (via Serial Input)
This project simulates a speech recognition system using the Arduino Serial Monitor. By sending text-based commands like "LED ON" or "LED OFF" through the Serial Monitor, you can control an LED. A buzzer is used to provide feedback.

🔧 Components Used:
Component	Quantity
Arduino Uno R3	1
LED (Red)	1
Buzzer (Active)	1
220Ω Resistor	1
10kΩ Resistor	1
Jumper Wires	As needed
Breadboard (optional)	1

🔌 Circuit Connections:
🔹 LED:
LED Pin	Arduino Pin
Anode (+)	Pin 8 (via 220Ω resistor)
Cathode (-)	GND

🔹 Buzzer:
Buzzer Pin	Arduino Pin
+ (Positive)	Pin 7
– (Negative)	GND

💻 Code Explanation:
cpp
Copy
Edit
String inputCommand = "";

void setup() {
    pinMode(8, OUTPUT);        // LED
    pinMode(7, OUTPUT);        // Buzzer
    Serial.begin(9600);
    Serial.println("Speech Recognition System Ready");
}

void loop() {
    if (Serial.available()) {
        inputCommand = Serial.readString();
        inputCommand.trim(); // Remove leading/trailing whitespace

        if (inputCommand == "LED ON") {
            digitalWrite(8, HIGH);   // Turn on LED
            digitalWrite(7, HIGH);   // Sound buzzer
            delay(200);
            digitalWrite(7, LOW);
            Serial.println("LED Turned ON");
        } 
        else if (inputCommand == "LED OFF") {
            digitalWrite(8, LOW);    // Turn off LED
            Serial.println("LED Turned OFF");
        }
        else {
            Serial.println("Command not recognized");
        }
    }
}
🧠 Project Purpose:
Mimics speech recognition via typed commands.

Basic serial communication project.

Introduces conditional control of components (LED + buzzer) via input strings.

Can be expanded to real speech recognition modules like Elechouse V3 or Google Assistant + ESP32.

🧪 Output Example:
In Serial Monitor:
pgsql
Copy
Edit
Speech Recognition System Ready
LED Turned ON
LED Turned OFF
🧰 Commands to Use:
LED ON → Turns on the LED and beeps the buzzer.

LED OFF → Turns off the LED.
