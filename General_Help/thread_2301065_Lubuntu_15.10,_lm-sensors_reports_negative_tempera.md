---
title: "Lubuntu 15.10, lm-sensors reports negative temperatures."
date: 2015-10-30
forum: General Help
---

### Post by spode2 on 2015-10-30
Can anyone confirm whether there is a problem with the IT87 module reading temperatures from an IT8721? I have been using pwmconfig to try and get the fans to run at a sensible speed but find the process confusing enough without getting these odd readings.

The sensors command returns this:

radeon-pci-0100
Adapter: PCI adapter
temp1:        +49.5°C  (crit = +120.0°C, hyst = +90.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +25.0°C  (high = +82.0°C, crit = +98.0°C)
Core 1:       +26.0°C  (high = +82.0°C, crit = +98.0°C)
Core 2:       +31.0°C  (high = +82.0°C, crit = +98.0°C)
Core 3:       +26.0°C  (high = +82.0°C, crit = +98.0°C)

it8721-isa-0a10
Adapter: ISA adapter
in0:          +0.85 V  (min =  +1.22 V, max =  +1.28 V)  ALARM
in1:          +3.00 V  (min =  +2.82 V, max =  +3.06 V)
in2:          +2.02 V  (min =  +2.94 V, max =  +2.26 V)  ALARM
+3.3V:        +3.34 V  (min =  +6.00 V, max =  +3.72 V)  ALARM
in4:          +3.00 V  (min =  +1.30 V, max =  +1.42 V)  ALARM
in5:          +2.22 V  (min =  +1.32 V, max =  +2.98 V)
in6:          +2.22 V  (min =  +0.77 V, max =  +2.98 V)
3VSB:         +3.36 V  (min =  +2.02 V, max =  +5.23 V)
Vbat:         +3.24 V  
fan1:        1339 RPM  (min =   10 RPM)
fan2:        1236 RPM  (min =   11 RPM)
temp1:        -28.0°C  (low  = -21.0°C, high = -43.0°C)  ALARM  sensor = thermal diode
temp2:         -7.0°C  (low  = -65.0°C, high =  -3.0°C)  sensor = thermistor
temp3:        -68.0°C  (low  = +123.0°C, high = -65.0°C)  sensor = Intel PECI
intrusion0:  ALARM

dell_smm-virtual-0
Adapter: Virtual device
Processor Fan:   1351 RPM
Motherboard Fan: 1245 RPM

Is there a way to correct this with entries in the etc/sensors3.conf file?

---

