---
title: "Lockups, overheating?"
date: 2007-05-22
forum: General Help
---

### Post by caecusum on 2007-05-22
I run an Ubuntu 7.04/Windows XP dual boot system.  Lately I've been getting really weird graphic artifacts and strange lockups, typically in that order.  It occurs most frequently when I am running something graphically intense, which lead me to believe that I might be having some overheating issues.  This occurs both in Windows and Ubuntu and it has persisted through an OS reinstallation.

Following the instructions on the Ubuntu guide I ran the lm-sensors program and got these results, which I am having some trouble deciphering:

> 
VCore 1:   +1.26 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
VCore 2:   +3.31 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:     +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:     +11.84 V  (min =  +0.00 V, max = +16.32 V)   ALARM
-12V:      +3.93 V  (min = -27.36 V, max =  +3.93 V)   ALARM
-5V:       +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:     +5.13 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:      +4.08 V
fan1:     2250 RPM  (min =    0 RPM, div = 4)          
fan2:        0 RPM  (min =    0 RPM, div = 128)          
fan3:        0 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +36°C  (low  =    -1°C, high =  +127°C)   sensor = diode   ALARM
CPU Temp:    +42°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   ALARM
Temp3:      +128°C  (low  =    -1°C, high =  +127°C)   sensor = disabled   



All those "ALARM" notes worry me.  My computer has a CoolerMaster liquid cooling system which I know little about.  Should I rip it apart and check the reservoir?  I don't even know if this is the problem, but it worries me.  Help, PLEASE!

---

### Post by scrooge_74 on 2007-05-22
Never use one of those cooling systems, try to ventilate better, take the case out for instance.  Put a fan close to the air intakes, move the PC to either a cooler spot or a more ventilated spot. 

Be carefull not to overheat it to often, in the short to medium term you are going to end with a damage mother board

---

### Post by TravMan63 on 2007-05-23
I'm unfamiliar with the lm-sensors program, but I'm wondering if perhaps you are misinterpreting the output?
If the voltages have indeed fluctuated that much, looks like a power supply problem.  Also running a graphics/cpu  intense program will cause power demands to go up, as well as the heat. 

The temperatures look ok, but the cpu temp does depend on what you're running. Check the manufactures website and [http://www.hardwaresecrets.com/article/143](http://www.hardwaresecrets.com/article/143) 

Overheating can definitely cause lockups.  So can improper voltages.  Your 5v reading looks like it's high.
Are you over clocking your system?

The rule of thumb for max case temperature is 45, your output is 36 (perhaps the alarm is set for 127? that's way too hot!)  A good case cleaning can help.

For Windows, you can install a free program called "motherboard monitor"

[http://www.majorgeeks.com/download.php?det=311](http://www.majorgeeks.com/download.php?det=311) - it will sound the internal pc speaker when an alarm condition is met.  (Can be configed to send an email as well)

I would run this as well and compare it's output to the readings in linux.  Also check in your system bios for temp readings.

TM

---

### Post by scrooge_74 on 2007-05-23
try typing  in a terminal acpi -t and see what it says

---

