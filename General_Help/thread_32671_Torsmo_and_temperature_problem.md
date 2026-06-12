---
title: "Torsmo and temperature problem"
date: 2005-05-08
forum: General Help
---

### Post by Chrysaor on 2005-05-08
Hi
I installed lm-sensors and detected sensors and loaded into my kernel modules.
Sensors command shows up fine, but when i try to use that in Torsmo i get the following errors:
```
torsmo: can't open '/sys/bus/i2c/devices/0-0050/temp1_input': No such file or directory
torsmo: can't open '/sys/bus/i2c/devices/0-0050/temp2_input': No such file or directory
```
What am i doing wrong here?

This is what i use to get temps in **.torsmorc**
```
${color grey}Temperatures: CPU:$color ${i2c temp 1}°C${color grey} - MB:$color ${i2c temp 2}°C
```

Here is my **sensors** output, everything seems to get detected fine.
```
w83697hf-isa-0290
Adapter: ISA adapter
VCore:     +1.74 V  (min =  +3.18 V, max =  +0.90 V)
+3.3V:     +3.23 V  (min =  +1.18 V, max =  +3.06 V)
+5V:       +5.03 V  (min =  +6.29 V, max =  +2.12 V)
+12V:     +11.80 V  (min = +12.22 V, max = +11.43 V)
-12V:     -11.78 V  (min = -13.02 V, max =  -7.10 V)
-5V:       -4.90 V  (min =  +1.33 V, max =  +0.53 V)
V5SB:      +5.38 V  (min =  +2.77 V, max =  +5.70 V)
VBat:      +3.38 V  (min =  +3.23 V, max =  +1.84 V)
fan1:     5487 RPM  (min = 4720 RPM, div = 2)
fan2:        0 RPM  (min = 3461 RPM, div = 2)
temp1:       +34°C  (high =    -3°C, hyst =    -1°C)   sensor = thermistor 
temp2:     +52.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor 
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-51
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256
```

---

### Post by Chrysaor on 2005-05-08
Solved this, getting temperatures fine now. :)

---

### Post by madverb on 2005-08-22
Thanks for the detailed fix for your problem... it really helped me out. Sarcasm never works well in text.

---

