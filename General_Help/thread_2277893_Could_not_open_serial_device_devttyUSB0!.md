---
title: "Could not open serial device /dev/ttyUSB0!"
date: 2015-05-12
forum: General Help
---

### Post by FU_NA on 2015-05-12
I am using ubundu 12.04, try to do Serial communication between arduino micro board and PC .I have checked that I'm a member of dialout group. so the error is like this : ]> [ WARN] [1431454109.213692440]: Service call for exploration service failed
[ WARN] [1431454113.213491338]: Service call for exploration service failed
[ WARN] [1431454117.213380953]: Service call for exploration service failed
[ WARN] [1431454121.213427291]: Service call for exploration service failed
^CRos shutdown, proceeding to close the gui.
acsc_nuc@localhost:~/catkin_ws/src/flight/src$ rosrun flight flight 
serialInit: Could not open serial device /dev/ttyUSB0!
Problem starting com port!
[ WARN] [1431454141.480160012]: Service call for exploration service failed
[ WARN] [1431454145.479981666]: Service call for exploration service failed
[ WARN] [1431454149.479896392]: Service call for exploration service failed
service failed  Help ,thanks.

---

### Post by dino99 on 2015-05-12
how have you made the installation ?
[http://forum.arduino.cc/index.php?topic=259351.0](http://forum.arduino.cc/index.php?topic=259351.0)

---

### Post by tgalati4 on 2015-05-12
You can install *setserial* and get some information about your serial port:

```
sudo apt-get install setserial
```

Then you can query the serial port to see what settings it is set to.

> tgalati4@Mint17 ~ $ setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: unknown, Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test


It helps to have the Arduino IDE serial settings match what your hardware serial port is set to.

---

### Post by FU_NA on 2015-05-12
> **tgalati4 said:**
> You can install *setserial* and get some information about your serial port:

```
sudo apt-get install setserial
```

Then you can query the serial port to see what settings it is set to.



It helps to have the Arduino IDE serial settings match what your hardware serial port is set to.

I can run the code when using arduino IDE ,which means that my serial port is connected.
However, when I try to run some files at terminal, it gives me this problem .

---

### Post by tgalati4 on 2015-05-12
Post your interrupts:

```
cat /proc/interrupts
```

---

### Post by FU_NA on 2015-05-12
> **tgalati4 said:**
> Post your interrupts:

```
cat /proc/interrupts
```

 Have a look at the attached image.

---

### Post by FU_NA on 2015-05-12
> **tgalati4 said:**
> Post your interrupts:

```
cat /proc/interrupts
```

By the way, I realize that the serial port at arduino IDE is called  "/dev/ttyACM0",which is different from the name given at the terminal  "/dev/ttyUSB0!".

---

### Post by HermanAB on 2015-05-13
Well, first you got to be sure about the name of the device.  There are two ways to get it:
$ dmesg
Plug it in
$ dmesg
See what USB related message you get.

You can also check the /dev directory:
$ ls /dev/tty*


USB serial devices are usually /dev/ttyUSBx, but some devices such as those by Moxa, may have different names.

---

### Post by FU_NA on 2015-05-13
> **HermanAB said:**
> Well, first you got to be sure about the name of the device.  There are two ways to get it: $ dmesg Plug it in $ dmesg See what USB related message you get.  You can also check the /dev directory: $ ls /dev/tty*   USB serial devices are usually /dev/ttyUSBx, but some devices such as those by Moxa, may have different names.  So does it mean that my device is ls /dev/ttyACM0???

---

