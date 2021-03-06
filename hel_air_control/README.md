## Helium & Air Control
Two components of our installation that are responsible for foam fabrication are air compressor and helium balloon. Each of these components has controllable valve that regulates a rate of either air or helium injected inside the machine. This valve has two states: opened or closed. Two questions arise: how to control it using Arduino board and how to produce different levels of injected substance having only two discrete states.

Since Arduino is capable to give out **5V** and the valves' motors are powered with the voltage **>> 5V**, it is impossible to control them using only Arduino board, which had to be extended with additional Hardware based on this scheme: http://bildr.org/2011/03/high-power-control-with-arduino-and-tip120/. Using a transistor it has become possible to simulate the switching function of Arduino board and control more powerful devices.

To produce different levels of injected substance we use PWM pins of Arduino board. This is the simplest way to achieve analog signals using digital means http://arduino.cc/en/Tutorial/PWM. Using
```java
analogWrite(0..255);
```
function it is possible to adjust the level of injected substance. Thus using PWM pins of Arduino board and extended Hardware we can easily control these two components.

This intuitive example demonstrates how we can control the level of air injection (helium injection can be done in the same manner). Using **Slider** element we choose how much air we want to inject using a rate *0..255*. Then we can send this value to Arduino using serial connection and a simple protocol which allows to detect when a complete message is received (in this case we send the PWM value and as an end delimiter we use char *a = air*).
