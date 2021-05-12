#include<LiquidCrystal.h>

LiquidCrystal lcd(A0, A1, 5, 4, 3, 2);

int triggerPin = 7;
int echoPin = 6;
unsigned long duration;
int distance;
int pinBuzzer =13;
int rPin =10;
int bPin =8;
int pirPin =12;
int isHuman =0;



void setup()
{
  pinMode(triggerPin, OUTPUT);
  pinMode (echoPin, INPUT);
  pinMode(pinBuzzer, OUTPUT);
  pinMode(rPin, OUTPUT);
  pinMode(bPin, OUTPUT);
  pinMode(pirPin, INPUT);
  Serial.begin(9600);
  
  lcd.begin(16, 2); 
   
}

void loop()
{
    
   
  
  isHuman = digitalRead(pirPin);
  Serial.println(isHuman);
  if (isHuman ==1){
    
	digitalWrite(triggerPin, LOW);
 	delayMicroseconds(2);
  //clearing the trigger
  	digitalWrite(triggerPin, HIGH);
  	delayMicroseconds(10);
  	digitalWrite(triggerPin, LOW);
  
  // capturing the time duration for sound wave to travel in microseconds
  	duration = pulseIn(echoPin, HIGH);
  	distance = 0.01723 * duration;
  	Serial.print(distance);
  	Serial.println("cm");
    
    if  (isHuman == 1 && distance < 200 ){
    
  
    digitalWrite(rPin, HIGH);
    digitalWrite(bPin, LOW);
    tone(pinBuzzer,293);
    lcd.clear();
    lcd.setCursor(0,0);          
  	lcd.print("   STAY!!"); 
  	lcd.setCursor(0,1);           
  	lcd.print("   AWAY!!");
    delay(200);    
    noTone(pinBuzzer);
    digitalWrite(rPin, LOW);
    lcd.clear();     
    
  }
  else {
  
    digitalWrite(rPin, LOW);
    digitalWrite(bPin, HIGH);
    lcd.setCursor(0,0);          
  	lcd.print(" You are safe"); 
  	lcd.setCursor(0,1);           
  	lcd.print("    ");
    
  }
    
    
  }
  
   
  
}
