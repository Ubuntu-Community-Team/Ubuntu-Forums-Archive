---
title: "lm-sensors and system2free superkaramba theme"
date: 2007-06-18
forum: General Help
---

### Post by AriciU on 2007-06-18
Hi

I'm trying to get the "system2free" superkaramba widget/theme to show the CPU temperature. The guy who made the theme had Fedora Core i think and used the "cat /proc/acpi/thermal_zone/THRM/temperature | grep 'temperature:' | sed -e 's/.*: //'" command to display the temperature. This doesn't work in Ubuntu.

I've installed lm-sensors and configured them correctly. The output i get when using "sensors" command is:

> it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.14 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:   +2.64 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:     +3.34 V  (min =  +0.00 V, max =  +4.08 V)
+5V:       +3.41 V  (min =  +0.00 V, max =  +6.85 V)
+12V:     +12.22 V  (min =  +0.00 V, max = +16.32 V)
-12V:      -5.15 V  (min = -27.36 V, max =  +3.93 V)
-5V:       -2.69 V  (min = -13.64 V, max =  +4.03 V)
Stdby:     +4.41 V  (min =  +0.00 V, max =  +6.85 V)
VBat:      +4.08 V
fan1:     3125 RPM  (min =    0 RPM, div = 8)
fan2:     2163 RPM  (min =    0 RPM, div = 8)
fan3:        0 RPM  (min =    0 RPM, div = 8)
M/B Temp:    +25°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor
CPU Temp:    +32°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor
Temp3:        -6°C  (low  =  +127°C, high =  +127°C)   sensor = diode


The one that interests me is obviously "CPU Temp". So... i've edited the system2free.theme and replaced the cat /proc/..................... line with "sensors | grep CPU Temp". The problem is that it displays everything correctly but there is too much text outputed and it messes up my system monitor theme.

Long story short...

How do i modify the output of the "sensors | grep 'CPU Temp'" command from **"CPU Temp:    +32°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor"** to just **"CPU Temp:   32°C"**. Without the "+" and the "(low  =  +127°C, high =  +127°C)   sensor = thermistor" after the value.


Thanks :)

---

### Post by AriciU on 2007-06-18
No one? :(

---

### Post by Shakarih on 2007-11-06
> "How do i modify the output of the "sensors | grep 'CPU Temp'" command from "CPU Temp: +32°C (low = +127°C, high = +127°C) sensor = thermistor" to just "CPU Temp: 32°C". Without the "+" and the "(low = +127°C, high = +127°C) sensor = thermistor" after the value."

Maybe this is coming a little bit late, but maybe late is better than ever

sensors | grep "CPU Temp" | cut -c 0-18 will do that trick :)

---

