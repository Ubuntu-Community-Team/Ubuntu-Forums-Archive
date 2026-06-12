---
title: "cpu mother board tempature program?"
date: 2008-04-22
forum: General Help
---

### Post by nacho32 on 2008-04-22
is their any way to monitor the cpu temperature and mother board temp in 7.10 ?

thanks

---

### Post by ahaslam on 2008-04-22
lm_sensors

You may want to add something like Conky if you also want values displayed & updated.

Example sensors output:

```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.38 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.30 V  (min =  +1.80 V, max =  +3.38 V)   ALARM
AVCC:        +3.33 V  (min =  +3.58 V, max =  +0.00 V)   ALARM
3VCC:        +3.33 V  (min =  +1.30 V, max =  +0.05 V)   ALARM
in4:         +1.19 V  (min =  +0.10 V, max =  +0.03 V)   ALARM
in5:         +1.66 V  (min =  +0.00 V, max =  +1.54 V)   ALARM
in6:         +4.02 V  (min =  +0.82 V, max =  +0.00 V)   ALARM
VSB:         +3.33 V  (min =  +0.26 V, max =  +2.30 V)   ALARM
VBAT:        +3.26 V  (min =  +2.05 V, max =  +2.05 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 128)  ALARM
CPU Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
Aux Fan:    1318 RPM  (min = 8437 RPM, div = 32)  ALARM
fan5:          0 RPM  (min =    0 RPM, div = 128)  ALARM
Sys Temp:    +37.0°C  (high =  +5.0°C, hyst = +64.0°C)  sensor = thermistor
CPU Temp:    +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +127.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +46.0°C  (crit = +100.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +44.0°C  (crit = +100.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +44.0°C  (crit = +100.0°C)
```

Example of conky setup:

[IMG]http://farm3.static.flickr.com/2199/2391591745_dcf194009a_o.png[/IMG]

;)

---

### Post by SnakeHips on 2008-04-22
:-)

you might like to take a look at conky 

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by ahaslam on 2008-04-22
Sorry SnakeHips, I have a bad habit of editing posts :/

---

