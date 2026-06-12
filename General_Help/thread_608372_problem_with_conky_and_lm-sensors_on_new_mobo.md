---
title: "problem with conky and lm-sensors on new mobo"
date: 2007-11-09
forum: General Help
---

### Post by m.musashi on 2007-11-09
Have there been any changes to how lm-sensors works or whether or not it's needed? I just changed my mobo (from msi k8ngm2 to asus k8n32 sli deluxe) and I'm no longer getting correct info - at least it doesn't look correct (i.e. the temp is very slow to change and in the past would move up quickly under stress). Also, I get no readout for the CPU fan speed as I did before. I did fully remove lm-sensors and reinstall and reconfigure using the same how to I used before on the forums. Here is the output of "sensors"

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +27°C
Core1 Temp:
             +29°C

it8712-isa-0d00
Adapter: ISA adapter
VCore 1:   +1.15 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:     +3.28 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +4.95 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.10 V  (min =  +0.00 V, max = +16.32 V)   
-12V:      +3.93 V  (min = -27.36 V, max =  +3.93 V)   ALARM
-5V:       +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:     +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:      +3.10 V
fan1:        0 RPM  (min =    0 RPM, div = 2)          
fan2:        0 RPM  (min =    0 RPM, div = 128)          
fan3:        0 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +33°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
CPU Temp:    +37°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
Temp3:      +128°C  (low  =    -1°C, high =  +127°C)   sensor = disabled
```

What I don't get is what's the right CPU temp? The temps for core 1 and core 2 are much lower than for "CPU Temp" further down. How do I configure conky to grab the right data? On the MSI board it used the i2c module but the asus seems to use the k8temp module and conky has no variable for k8temp that I can find.

Thanks.

---

### Post by m.musashi on 2007-11-10
After some stress testing last night, I noticed that the fan speed would print in conky if it was running full speed. When the mobo slows it down (I think that is the Asus Q-fan that does that) conky (and sensors) no longer registers the speed. Maybe it's a BIOS issue. I would update the BIOS but I don't have windows or a floppy drive.

---

