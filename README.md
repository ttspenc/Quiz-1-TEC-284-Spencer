# Quiz-1-TEC-284-Spencer
// int pins
int redButton = 2;
int greenButton = 3;
int blueButton = 4;
// int leds 
int redLED = 9;     
int greenLED = 10;
int blueLED = 11;

// setup
void setup() {
  // use pullup for buttons
  pinMode(redButton, INPUT_PULLUP);
  pinMode(greenButton, INPUT_PULLUP);
  pinMode(blueButton, INPUT_PULLUP);

  // LED as output
  pinMode(redLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(blueLED, OUTPUT);

  Serial.begin(9600);
  Serial.println("System started");  

  
}

// Loop 
void loop() {
  displayRGBLED();  
}

// read buttons 
void displayRGBLED() {
  // Read button states
  int redState = digitalRead(redButton);
  int greenState = digitalRead(greenButton);
  int blueState = digitalRead(blueButton);

  // LED off
  digitalWrite(redLED, LOW);
  digitalWrite(greenLED, LOW);
  digitalWrite(blueLED, LOW);

  // when multiple buttons are pressed, different colors
  if (redState == LOW && blueState == LOW && greenState == LOW)
  {
    digitalWrite(redLED, HIGH);
    digitalWrite(blueLED, HIGH);
    digitalWrite(greenLED, HIGH);
  }
  // purple
  else if(redState == LOW && blueState == LOW)
  {
    digitalWrite(redLED, HIGH);
    digitalWrite(blueLED, HIGH);
    Serial.print("Purple ON");

  }
    
  else
  {

    // buttons start low, when pressed led high
      if (redState == LOW) 
      {
        digitalWrite(redLED, HIGH);
        Serial.println("Red ON");
      }
      if (greenState == LOW) 
      {
        digitalWrite(greenLED, HIGH);
        Serial.println("Green ON");
      }
      if (blueState == LOW) 
      {
        digitalWrite(blueLED, HIGH);
        Serial.println("Blue ON");
      }

  }

  
  
}
