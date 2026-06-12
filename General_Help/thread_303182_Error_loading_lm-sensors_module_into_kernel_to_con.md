---
title: "Error loading lm-sensors module into kernel to control fans"
date: 2006-11-19
forum: General Help
---

### Post by Bastanteroma on 2006-11-19
I followed the instructions here - [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)
to setup lm-sensors and get control over my fan speeds.

But when I type in sensors, or sensors -s I get this message:

Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

As far as I know, everything seemed to work ok until then.  When I entered sudo sensors-detect a few sensors seemed to be detected.

These instructions got sensors working, but pwmconfig couldn't adjust my fan.  Oh well.
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

