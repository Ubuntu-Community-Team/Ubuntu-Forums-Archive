---
title: "Cpu heat"
date: 2006-12-09
forum: General Help
---

### Post by glasyalabolis on 2006-12-09
Hi all, I was wondering if anyone knew of any programs that would let me monitor my cpu's heat and possibly fan speed. I tried this feature in my motherboard to overclock my cpu and my video card and  am trying to figure out if it works.
```
cat /proc/cpuinfo
```
still gives me my old cpu frequency and dosen't give me heat or anything else.
Any help would be appreciated, thanks in advance :)

---

### Post by stewjack on 2006-12-09
> **glasyalabolis said:**
> Hi all, I was wondering if anyone knew of any programs that would let me monitor my cpu's heat and possibly fan speed. 

I would be interested in the same thing.  My CPU is usually running near 100% load on Windows because I donate my excess CPU cycles to BOINC distributed computing.  On Windows I use SpeedFan 4.28.:) 

Jack

---

### Post by haxer on 2006-12-09
Swiftbox? :-k

---

### Post by john.nicholls on 2006-12-09
lm-sensors

John

---

### Post by hytek on 2006-12-09
doesn't gdesklets have this also? (or gwidgets...forget name :rolleyes: )

---

### Post by fragos on 2006-12-10
lm-sensors is the kernel level interface to temp and other goodies.  Add the applet "Hardware Sensors Monitor" to have a constant view of the data.

---

### Post by Rodneyck on 2006-12-10
Here you go...

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)

---

