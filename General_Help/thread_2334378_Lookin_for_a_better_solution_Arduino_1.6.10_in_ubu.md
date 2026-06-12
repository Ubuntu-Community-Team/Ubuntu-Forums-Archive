---
title: "Lookin for a better solution: Arduino 1.6.10 in ubuntu 16.04 using sparkfun add ons"
date: 2016-08-19
forum: General Help
---

### Post by soulsurfer2 on 2016-08-19
So tonight I was working through the hackerbox9 box of goodies. I was working with a sparkfun pro micro and attempting to connect it to my computer.  I'm using ubuntu 16.04 and  arduino IDE ver 1.6.10.  
  My initial problem using the code :

> /* Pro Micro Test Code   by: Nathan Seidle
   modified by: Jim Lindblom
   SparkFun Electronics
   date: September 16, 2013
   license: Public Domain - please use this code however you'd like.
   It's provided as a learning tool.

   This code is provided to show how to control the SparkFun
   ProMicro's TX and RX LEDs within a sketch. It also serves
   to explain the difference between Serial.print() and
   Serial1.print().
*/

int RXLED = 17;  // The RX LED has a defined Arduino pin
// The TX LED was not so lucky, we'll need to use pre-defined
// macros (TXLED1, TXLED0) to control that.
// (We could use the same macros for the RX LED too -- RXLED1,
//  and RXLED0.)

void setup()
{
 pinMode(RXLED, OUTPUT);  // Set RX LED as an output
 // TX LED is set as an output behind the scenes

 Serial.begin(9600); //This pipes to the serial monitor
 Serial1.begin(9600); //This is the UART, pipes to sensors attached to board
}

void loop()
{
 Serial.println("Hello world");  // Print "Hello World" to the Serial Monitor
 Serial1.println("Hello!");  // Print "Hello!" over hardware UART

 digitalWrite(RXLED, LOW);   // set the LED on
 TXLED0; //TX LED is not tied to a normally controlled pin
 delay(1000);              // wait for a second
 digitalWrite(RXLED, HIGH);    // set the LED off
 TXLED1;
 delay(1000);              // wait for a second
}

Using this code while under normal user environment yielded this debug:
> processing.app.debug.RunnerException	at cc.arduino.packages.uploaders.SerialUploader.uploadUsingPreferences(SerialUploader.java:162)
	at cc.arduino.UploaderUtils.upload(UploaderUtils.java:78)
	at processing.app.Sketch.upload(Sketch.java:1187)
	at processing.app.Sketch.exportApplet(Sketch.java:1160)
	at processing.app.Sketch.exportApplet(Sketch.java:1132)
	at processing.app.Editor$DefaultExportHandler.run(Editor.java:2409)
	at java.lang.Thread.run(Thread.java:745)
Caused by: processing.app.SerialException: Error touching serial port '/dev/ttyACM0'.
	at processing.app.Serial.touchForCDCReset(Serial.java:87)
	at cc.arduino.packages.uploaders.SerialUploader.uploadUsingPreferences(SerialUploader.java:146)
	... 6 more
Caused by: jssc.SerialPortException: Port name - /dev/ttyACM0; Method name - openPort(); Exception type - Permission denied.
	at jssc.SerialPort.openPort(SerialPort.java:170)
	at processing.app.Serial.touchForCDCReset(Serial.java:81)
	... 7 more

I immediately had one of 2 reactions, its either a java error, a permissions error.
There are a few threads out there that suggest correcting this error by adding the user to the dialout user group.
 This failed.  It actually produced the same error code.

This is the part I'm not comfortable with.  I sudoed arduinoes IDE and then implemented all of sparkfun's hardware definitions...  It worked.  
I'd rather not do this to make it work.  

It feels like theres a better way to make it work without exposing a system by using root user permissions.

Any ideas?

---

### Post by wildmanne39 on 2016-08-19
*Thread moved to **General Help**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

