---
title: "Grabbing (Grepping) Values From (lm-)Sensors"
date: 2007-12-09
forum: General Help
---

### Post by Brando569 on 2007-12-09
hey everyone, i found a cool system monitor over at kde-look.org but when i downloaded it and opened it (its a karamba widget) most of the sensors didnt work. after a while of messing around with it i have about 90% of them working, theres a few though that i have no idea about.

first off im trying to grep the values from the command sensors -f, this is my output from it since it will most likely help:
```
bran@ra:~$ sensors -f
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +79°F
Core1 Temp:
             +93°F

it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.31 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:   +1.18 V  (min =  +1.28 V, max =  +1.68 V)   ALARM
+3.3V:     +3.33 V  (min =  +2.78 V, max =  +3.78 V)
+5V:       +5.05 V  (min =  +4.49 V, max =  +5.48 V)
+12V:     +12.03 V  (min =  +9.98 V, max = +13.95 V)
-12V:     -15.95 V  (min = -22.94 V, max = -17.05 V)   ALARM
-5V:       -2.21 V  (min =  -9.14 V, max =  -7.75 V)   ALARM
Stdby:     +5.08 V  (min =  +4.49 V, max =  +5.48 V)
VBat:      +3.09 V
fan1:     2311 RPM  (min =  811 RPM, div = 8)
fan2:      937 RPM  (min =  811 RPM, div = 8)
fan3:     3590 RPM  (min =  811 RPM, div = 8)
M/B Temp:    +84°F  (low  =  +261°F, high =  +163°F)   sensor = diode
CPU Temp:   +100°F  (low  =  +261°F, high =  +163°F)   sensor = thermistor
Temp3:      +111°F  (low  =  +261°F, high =  +163°F)   sensor = thermistor
```

the problems i have are with Core 0 and 1 Temps (since the actual temps are on separate lines then their labels), the negative leads (rails) of the PSU (-12V and -5V) (when i issue grep '-12V' it gives me the info for grep, since it thinks that the -  is the beginning of an option) and this isnt really a problem but i have no idea what temp3 is for, is there a way to find out what device it is monitoring?

these are the commands im using to grep the values:
For Core 0 im using this:
```
program="sensors -f | grep 'Core0 ' | awk '{print $1 $2}'"
```

i substituted the awk in for what was originally there which was this:

```
program="sensors -f | grep 'Core1' | cut -d + -f 2 | cut -d ' ' -f 1"
```

the first one gives me this output: Core0Temp:

while the second one gives me this: Core1

i tried to figure out how to use cut but it confused me so i tried awk instead which worked for most of the other values


As for the problems with the PSU rails this is what im using:
```
sensors | grep '-12V' | awk '{print $2}'"
```

and it just gives me the info about grep as if i had just typed grep -V, if i remove the V and just use 'grep -12' it thinks its an option and tells me to check the man pages for available options


thanks in advance

---

### Post by der_joachim on 2007-12-09
I think that grep is confused by the dash. You should call grep with a proper regular expression (the -e option), thus making it possible to escape the dash. Try something like the following: 
```
sensors | grep -e \-12V | awk '{print $2}'"
```

Good luck.

---

### Post by Brando569 on 2007-12-09
Danke, der_joachim :) that worked, now if i can only figure out how to grep the core temp values ill be set

---

