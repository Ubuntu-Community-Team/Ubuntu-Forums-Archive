---
title: "sensors -s can't access procfs/sysfs file"
date: 2007-01-08
forum: General Help
---

### Post by MagisterJoe on 2007-01-08
I followed the 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29")

Ubuntuguide.org page on installing lm_sensors and using them.  Sensor detect worked fine, but when I **sudo sensors -s** to load to the kernel I get this error message:

[INDENT]Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
[/INDENT]

Any idea how to fix this?

---

### Post by MagisterJoe on 2007-01-08
Anyone at all?

Seems like no one answers tricky questions here anymore - they just bash newbies who complain about things or spout off about why they use Linux.

---

### Post by jharr on 2007-01-21
word, I'm having the same problem here.

---

### Post by Shatrat on 2007-01-21
What do you get from lsmod?
Maybe try lsmod | grep i2c?

---

### Post by david_2001 on 2007-01-21
I just did a pain-free two-step set-up of lm-sensors on edgy.  No special scripts or other tinkering were necessary.    Of course, this will only work if your motherboard is supported by lm-sensors.
[LIST=1]
[*]Run **sudo sensors-detect**, accepting all of the defaults except for the last.  The final default is to not modify /etc/modules whereas that's actually what you want to do.
[*]Restart.
[/LIST]
It really was that easy 8)!  All I've done since is edit /etc/sensors.conf to assign meaningful labels to the fans and the temperature sensors.

---

