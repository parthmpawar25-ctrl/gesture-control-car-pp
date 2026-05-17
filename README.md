# gesture-control-car-pp
// Motor Driver Pins
int ENA = 5;
int IN1 = 6;
int IN2 = 7;
int ENB = 9;
int IN3 = 10;
int IN4 = 11;

char data;

void setup() {

  pinMode(ENA, OUTPUT);
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);

  pinMode(ENB, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  Serial.begin(9600);

  analogWrite(ENA, 200);
  analogWrite(ENB, 200);
}

void loop() {

  if (Serial.available()) {

    data = Serial.read();

    if (data == 'F') {
      forward();
    }

    else if (data == 'B') {
      backward();
    }

    else if (data == 'L') {
      left();
    }

    else if (data == 'R') {
      right();
    }

    else if (data == 'S') {
      stopMotor();
    }
  }
}

void forward() {

  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);

  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

void backward() {

  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);

  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void left() {

  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);

  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

void right() {

  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);

  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void stopMotor() {

  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);

  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
}