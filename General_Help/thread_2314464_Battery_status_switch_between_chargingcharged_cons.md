---
title: "Battery status switch between charging/charged constantly after upgrading to 15.10"
date: 2016-02-21
forum: General Help
---

### Post by drohhyn2 on 2016-02-21
[COLOR=#111111][FONT=Ubuntu]I've upgraded from ubuntu 15.04 to 15.10 just some days ago. Now I see that the battery indicator always switches every second between the notebook's and the mouse's battery. The notebook's battery in constantly at 97% and charging, when I plug the power cord off it stops switching to the mouse's battery. After running [/FONT][/COLOR]acpi -V[COLOR=#111111][FONT=Ubuntu] several times, I've realized that the status is changing to "unknown" sometimes:

```
user@ubuntu:~$ acpi -V
Battery 0: Charging, 97%, 73:00:00 until charged
Battery 0: design capacity 4400 mAh, last full capacity 3314 mAh = 75%
Adapter 0: on-line
Thermal 0: ok, 44.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 95.0 degrees C
Thermal 1: ok, 44.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 100.0 degrees C
Cooling 0: x86_pkg_temp no state information available
Cooling 1: intel_powerclamp no state information available
Cooling 2: LCD 11 of 15
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: Processor 0 of 10
user@ubuntu:~$ acpi -V
Battery 0: Unknown, 97%
Battery 0: design capacity 4400 mAh, last full capacity 3314 mAh = 75%
Adapter 0: on-line
Thermal 0: ok, 44.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 95.0 degrees C
Thermal 1: ok, 44.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 100.0 degrees C
Cooling 0: x86_pkg_temp no state information available
Cooling 1: intel_powerclamp no state information available
Cooling 2: LCD 11 of 15
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: Processor 0 of 10
```

The problem does not occur on Windows 10 (dual boot). My machine is a Dell XPS 15Z.

(I have asked the same question [somewhere else]("https://askubuntu.com/questions/732844/battery-status-switch-between-charging-charged-constantly-after-upgrading-to-15").)

---

