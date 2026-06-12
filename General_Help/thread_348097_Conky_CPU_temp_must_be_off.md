---
title: "Conky CPU temp must be off"
date: 2007-01-28
forum: General Help
---

### Post by jhenager on 2007-01-28
I have had conky installed for a while, and everything looks ok except my CPU temperature commonly reads 1 to 13 degrees.
Here is the output from 'sensors'.
jeff@jeff-desktop:~$ sensors
it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.30 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +1.58 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +3.71 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +5.00 V  (min =  +4.76 V, max =  +5.24 V)
+12V:      +6.08 V  (min = +11.39 V, max = +12.61 V)   ALARM
-12V:      -2.20 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:       -3.11 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +4.78 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +3.28 V
fan1:     1117 RPM  (min =    0 RPM, div = 8 )
fan2:        0 RPM  (min = 3013 RPM, div = 8 )
fan3:        0 RPM  (min = 3013 RPM, div = 8 )
M/B Temp:    +48°C  (low  =   +15°C, high =   +40°C)   sensor = diode
CPU Temp:    +52°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
Temp3:       +37°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor
---------------------------------------------------------------------------------------------------------------------------------
I need to know how to offset it to get it closer to reality. I am running a Pentium D 820 on a PC Chips P23G motherboard.
Any help would be appreciated. 
Jeff

---

### Post by MkfIbK7a on 2007-01-28
is it in farenhieght or centigrade?

---

### Post by jhenager on 2007-01-28
> **wert613 said:**
> is it in farenhieght or centigrade?

C

---

### Post by MkfIbK7a on 2007-01-28
yes you are right either your comuter is at near freezing temperature or something is wrong with conky

---

### Post by jhenager on 2007-01-28
> **wert613 said:**
> yes you are right either your comuter is at near freezing temperature or something is wrong with conky
yes

---

### Post by jhenager on 2007-01-31
so nobody knows how to enter an offset to compensate for the incorrect reading?

---

