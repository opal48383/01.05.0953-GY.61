# 01.05.0953-GY.61
int Bx=0;
int By=0;
int Bz=0;//befor
int Lx=0;//later
int Ly=0;
int Lz=0;
void setup() {
  pinMode(A1,INPUT);
  pinMode(A2,INPUT);
  pinMode(A3,INPUT);
  pinMode(4,OUTPUT);//x+
  pinMode(5,OUTPUT);//x-
  pinMode(8,OUTPUT);//y+
  pinMode(9,OUTPUT);//y-
  Serial.begin(9600);
  delay(100);
  Serial.println("初始化");
  delay(100);
  Bx = analogRead(A1);
  By = analogRead(A2);
  Bz = analogRead(A3);
}

void loop() {
  Lx = analogRead(A1);
  Ly = analogRead(A2);
  Lz = analogRead(A3);
  Serial.println(" X      Y      Z");
  Serial.print(Lx);
  Serial.print("    ");
  Serial.print(Ly);
  Serial.print("    ");
  Serial.println(Lz);
  
  if(abs(Lx-Bx) >= 6){
    if(Lx-Bx > 0) {
      digitalWrite(4,LOW);
      digitalWrite(5,HIGH);
    }
    else {
      digitalWrite(4,HIGH);
      digitalWrite(5,LOW);
    }
  }
  else {
    digitalWrite(4,HIGH);
    digitalWrite(5,HIGH);
  }
  
  if(abs(Ly-By) >= 6){
    if(Ly-By > 0) {
      digitalWrite(8,LOW);
      digitalWrite(9,HIGH);
    }
    else {
      digitalWrite(8,HIGH);
      digitalWrite(9,LOW);
    }
  }
  else {
      digitalWrite(8,HIGH);
      digitalWrite(9,HIGH);
  }
  Bx = analogRead(A1);
  By = analogRead(A2);
  Bz = analogRead(A3);
  delay(200);
}
