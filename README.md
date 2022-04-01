# APP3
## About the project
<p>Our project is done as a work project for the engineering school of Télécom Saint-Etienne.</p>

<p> Code Arduino <p>
<p>#include <Arduino.h>

<p>void setup() {
<p>  // put your setup code here, to run once:
<p>  Serial.begin(9600);
<p>  delay(10000);
<p>}

void loop() {
  // put your main code here, to run repeatedly:
  const float T0=25+273.15; //Température de référence soit 25°C
  // Ici en Kelvin
  const float RT0=10000.0;//Résistance de la thermitance à 25°C
  const float R0=11960.0; // Résistance
  const float Beta=3977.0; //Constante béta
  uint16_t Mesure;
  float T;

  Mesure=analogRead(A0);

  T= 1/((1/T0)+((1/Beta)*log((R0/RT0)*((1024.0/(Mesure-13.0))-1)))); //Température en Kelvin
  T=T-273.15; //Conversion en °C

  Serial.println(Mesure-13.0);
  Serial.print("T = ");
  Serial.println(T);
}
 
