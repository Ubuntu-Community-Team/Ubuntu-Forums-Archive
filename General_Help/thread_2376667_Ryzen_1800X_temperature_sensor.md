---
title: "Ryzen 1800X temperature sensor"
date: 2017-11-04
forum: General Help
---

### Post by Osmodivs on 2017-11-04
i have a Ryzen 7 1700 and with* cat /proc/cpuinfo* it shows me that I have 16 cores, but with sensors command only gives me 1 core temp:
[I]asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM[/I]

lm-sensors only gives me this sensor:
[I]Driver `lm78':
  * ISA bus, address 0x290
    Chip `National Semiconductor LM78' (confidence: 6)[/I]

Is my chip not Linux ready?

---

### Post by QIII on 2017-11-04
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2354782](https://ubuntuforums.org/showthread.php?t=2354782)

As for temperature, AMD only returns a single temperature, not per core temps.  That is the nature of AMD CPUs and does not indicate a hardware or sensor failure.

---

