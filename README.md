The Morse Code Beacon project uses an Arduino to transmit messages via Morse code using an LED or buzzer. This project is ideal for learning the basics of electronics, communication systems, and programming. You can transmit predefined messages in Morse code, which consists of a series of dots (short signals) and dashes (long signals). The project offers flexibility for customization and is perfect for educational or signaling purposes.

Features
Transmits Morse code messages with LED or buzzer.
Customizable message and timing for dots, dashes, and pauses.
Expandable with additional components (e.g., buttons, displays).
Components Required
Arduino Uno (or compatible board)
LED (or buzzer)
220Ω Resistor (for LED)
Breadboard
Jumper wires
USB Cable
Computer with Arduino IDE
Circuit Diagram
LED Connection:

Connect the positive leg of the LED to a digital pin (e.g., Pin 13) via a 220Ω resistor.
Connect the negative leg of the LED to GND.
Buzzer (Optional):

Connect the positive leg of the buzzer to a digital pin, and the negative leg to GND.
Installation
Clone the repository:
bash
Copy code
git clone https://github.com/yourusername/morse-code-beacon.git
Open the project in the Arduino IDE.
Connect your Arduino to your computer.
Upload the code to the Arduino.
Usage
Set up the circuit as per the Circuit Diagram.
Upload the code to the Arduino.
The LED (or buzzer) will transmit the default Morse code message ("SOS").
Customization
To change the Morse code message, modify the loop() function in the Arduino sketch:

cpp
Copy code
void loop() {
  sendMorse("HELLO");  // Replace "HELLO" with your message
  delay(wordGap);
}
You can also adjust the timing of the signals by modifying the dotTime, dashTime, charGap, and wordGap variables.

Code Example
cpp
Copy code
int ledPin = 13;
int dotTime = 200;   
int dashTime = 600;  
int charGap = 600;  
int wordGap = 1400;

const String morseCode[] = {
  ".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---", 
  "-.-", ".-..", "--", "-.", "---", ".--.", "--.-", ".-.", "...", "-",   
  "..-", "...-", ".--", "-..-", "-.--", "--..", "-----", ".----", "..---", 
  "...--", "....-", ".....", "-....", "--...", "---..", "----."
};

void blinkMorse(char signal) {
  if (signal == '.') {
    digitalWrite(ledPin, HIGH);
    delay(dotTime);
  } else if (signal == '-') {
    digitalWrite(ledPin, HIGH);
    delay(dashTime);
  }
  digitalWrite(ledPin, LOW);
  delay(dotTime);
}

void sendMorse(String code) {
  for (int i = 0; i < code.length(); i++) {
    blinkMorse(code[i]);
  }
  delay(charGap);
}

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  sendMorse("SOS");
  delay(wordGap);
}
Future Enhancements
Add buttons to input custom messages.
Implement an LCD display to show the current message.

