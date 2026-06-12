---
title: "lm-sensors and X Sensors"
date: 2006-12-02
forum: General Help
---

### Post by Scottla on 2006-12-02
My PC is OC'd and I would like to access readings from lm-sensors (temps, fan speeds, etc.).  I installed X Sensors from the APPLICATIONS > ADD menu and it is now in the menus.  When I click on it, however, nothing happens, at least that I can see.

Did some reading and the app requires lm-sensors.  I checked in SYNAPTIC and it is showing installed.  There were two MARKED SUGGESTED FOR INSTALLATION with that package and I went ahead and installed them.  This did not help.

Anyone out there using this app or know how to access the lm-sensor data?  Want it on my desktop where I can watch it.

Thanks for your help!

---

### Post by Scottla on 2006-12-03
If no one here is familiar with these apps, can anyone suggest another great ubuntu user forum I might try?  Thanks!

---

### Post by autocrosser on 2006-12-03
Greetings--have you looked at the How-To for lm-sensors? A very complete guide was made back about a year or two ago & it still works for Edgy--just search for lm-sensors in the howto area

---

### Post by scxtt on 2006-12-03
did you load the module into the kernel?

i use:

**sudo modprobe w83627hf**

and get output like:

```
:> sensors -f
w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.41 V  (min =  +1.94 V, max =  +1.94 V)       ALARM
+12V:     +11.73 V  (min = +10.82 V, max = +13.19 V)
+3.3V:     +3.06 V  (min =  +3.14 V, max =  +3.47 V)       ALARM
+5V:       +5.01 V  (min =  +4.75 V, max =  +5.25 V)
-12V:      +6.06 V  (min = -10.80 V, max = -13.18 V)       ALARM
V5SB:      +4.97 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +1.31 V  (min =  +2.40 V, max =  +3.60 V)       ALARM
fan1:        0 RPM  (min =   -1 RPM, div = 128)              ALARM
CPU Fan:  2884 RPM  (min =   -1 RPM, div = 2)              ALARM
fan3:     2616 RPM  (min = 84375 RPM, div = 4)              ALARM
M/B Temp:    +88°F  (high =   +45°F, hyst =   +32°F)   sensor = thermistor   ALARM
CPU Temp: +125.6°F  (high =  +176°F, hyst =  +167°F)   sensor = thermistor
temp3:     +59.9°F  (high =  +176°F, hyst =  +167°F)   sensor = thermistor
vid:      +0.275 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm enabled
```

---

