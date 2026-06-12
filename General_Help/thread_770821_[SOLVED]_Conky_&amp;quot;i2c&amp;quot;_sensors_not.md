---
title: "[SOLVED] Conky &amp;quot;i2c&amp;quot; sensors not reading after upgrade"
date: 2008-04-27
forum: General Help
---

### Post by markjensen on 2008-04-27
My upgrade to 8.04 went well, but my sensors are no longer properly reading in Conky.

My i2c fans register as 0.   Temps 0.

However, when I do a **sensors** command, everything shows up.> mark@mark-core2:~$ sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.21 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +12.20 V  (min =  +2.32 V, max =  +3.43 V)   ALARM
AVCC:        +3.25 V  (min =  +0.83 V, max =  +2.94 V)   ALARM
3VCC:        +3.25 V  (min =  +2.70 V, max =  +0.10 V)   ALARM
in4:         +1.64 V  (min =  +0.26 V, max =  +0.12 V)   ALARM
in5:         +1.60 V  (min =  +0.21 V, max =  +1.15 V)   ALARM
in6:         +5.20 V  (min =  +1.02 V, max =  +4.99 V)   ALARM
VSB:         +3.25 V  (min =  +0.10 V, max =  +2.59 V)   ALARM
VBAT:        +3.20 V  (min =  +2.72 V, max =  +0.90 V)   ALARM
Case Fan:   1748 RPM  (min = 84375 RPM, div = 4)  ALARM
CPU Fan:    1125 RPM  (min = 3515 RPM, div = 8)  ALARM
Aux Fan:       0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +32.0 C  (high = +98.0 C, hyst = +37.0 C)  sensor = thermistor
CPU Temp:    +47.0 C  (high = +80.0 C, hyst = +75.0 C)  sensor = diode
AUX Temp:     +7.0 C  (high = +80.0 C, hyst = +75.0 C)  sensor = thermistor
cpu0_vid:   +1.388 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0 C  (crit = +85.0 C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0 C  (crit = +85.0 C)                  

mark@mark-core2:~$ Anyone have insight on why this stopped working, and how I can repair this?

---

### Post by markjensen on 2008-04-27
I have worked around this problem by replacing the non-functioning i2c calls with execi instructions that perform tasks like
**sensors |grep  'Case Fan'|cut -c13-16**

A second-best solution, but it displays.  Not sure what happened to my i2c sensor calls...:confused:

---

### Post by troutbum13 on 2008-07-30
same problem, anyone know a better fix than running the execi calls?

---

### Post by tamoneya on 2008-07-30
> **troutbum13 said:**
> same problem, anyone know a better fix than running the execi calls?

what is the output of :```
ls -l /sys/bus/i2c/devices/
```

---

### Post by markjensen on 2008-07-30
Hey!   After 3 months, responses!  :D

```
mark@mark-core2:~$ ls -l /sys/bus/i2c/devices/
total 0
mark@mark-core2:~$ 
```Looks like no i2c devices are available, for what it is worth.

---

### Post by tamoneya on 2008-07-30
okay well that is a start.  I am having the same problem and Im working on it.  I wanted to confirm that it was the same reason.  However I am also responseless.

[http://ubuntuforums.org/showthread.php?p=5491604#post5491604](http://ubuntuforums.org/showthread.php?p=5491604#post5491604)

I am going to try and do some more researching tomorrow and I will post some results.

EDIT:  Incase you want to do some research as well I am planning on trying out the hwmon variable instead of the i2c variable.  They are documented here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by troutbum13 on 2008-07-31
FWIW, I have tried to use the hwmon callout instead of ic2, no joy.

I have detected the sensors and added the kernel drivers to /etc/modules, but when I run sensors, I still get no results returned.

Was working fine in Gutsy?? I even compared /etc/modules between them and they are identical....

---

### Post by tamoneya on 2008-07-31
> **troutbum13 said:**
> FWIW, I have tried to use the hwmon callout instead of ic2, no joy.

I have detected the sensors and added the kernel drivers to /etc/modules, but when I run sensors, I still get no results returned.

Was working fine in Gutsy?? I even compared /etc/modules between them and they are identical....

Do you have nothing in /sys/bus/i2c/devices/ as well as me and markjensen?

---

### Post by tamoneya on 2008-07-31
I tried hwmon and platform and I managed to get hwmon to work.  While poking through directories I ran this command and got an interesting result:```
cat /sys/class/hwmon/hwmon1/device/temp1_label 
Core 0

```
and when I used hwmon2 instead of hwmon1 i found my other core ( i have a c2d).  So I added this code to conky and it worked.
```
${color #888888}Core 0: ${color #CCCCCC}${hwmon 1 temp 1} C  ${color #888888}Core 1: ${color #CCCCCC}${hwmon 2 temp 1} C
```

I then confirmed that this code actually works by running conky and then while keeping my eye on the temps I ran:```
sensors
```The numbers matched up exactly with the core temperatures.


If the first command returns the same result as I got or something similar you should try out hwmon.

---

### Post by Belarios on 2008-08-11
Looks like they moved em.  This works for me in .conkyrc
```
${color grey}Temperatures (C):
 ${color grey}CPU:$color ${platform it87.552 temp 1}
 ${color grey}NB:$color ${platform it87.552 temp 2}
 ${color grey}Case:$color ${platform it87.552 temp 3}
${color grey}Fan Speeds (RPM):
 ${color grey}CPU:$color ${platform it87.552 fan 1}
 ${color grey}Case:$color ${platform it87.552 fan 2}
 ${color grey}GPU:$color ${platform it87.552 fan 3}
```
but you should do a 
```
ls /sys/devices/platform
```
to check the name of your chip and change the above accordingly.

Found it over here: [http://forums.opensuse.org/archives/sf-archives/software/341306-conky-lm_-sensors-no-sys-bus-i2c-devices-solved.html](http://forums.opensuse.org/archives/sf-archives/software/341306-conky-lm_-sensors-no-sys-bus-i2c-devices-solved.html)

---

### Post by markjensen on 2008-08-11
Oooh, thank you!   I will try this when I get back home after work!

---

### Post by markjensen on 2008-08-11
Yup!  That did the trick for me!  Thanks!

My new two lines in .conkyrc are```
${color lightgrey}CPU:$color ${platform w83627ehf.656 temp 2}°C ${color grey} - MB:$color ${platform w83627ehf.656 temp 1}°C - GPU:$color ${execi 1 nvidia-settings -q gpucoretemp |grep ')'|cut -c45-46}°C
${color lightgrey}Fans: CPU:$color ${platform w83627ehf.656 fan 2} RPM${color grey} - Chasis:$color ${platform w83627ehf.656 fan 1} RPM${color grey}
```
(I happened to use the same w83627 module/sensors chipset)

---

