---
title: "cannot get pwmconfig working"
date: 2021-04-17
forum: General Help
---

### Post by nan0scho1ar on 2021-04-17
I have a server running ubuntu 20.04.2 and I'm trying to get fan control working using lm-sensors and fancontrol.

I have run sensors detect and confirmed it correctly detected the sensor modules in my server.
I have added the required lines to /etc/modules and ran `/etc/init.d/kmod start`.
When the next step failed I also tried restarting the machine.

When I tried to run `sudo pwmconfig` it correctly listed the devices
```Found the following devices:
    hwmon0 is 1350bb
    hwmon1 is coretemp
    hwmon2 is coretemp
    hwmon3 is nct7904
```
This all looks correct and matches what worked on this system previously.
However when it tried to ramp the fans up and down, each of the devices said "Device or resource busy".
Then at the end it said "No usable pwm outputs".

When I tried to find what was using each of these devices in /sys/devices/platform using `lsof` it didn't return anything meaningful.

I know for a fact that these devices can be pwm controlled because I have previously set up fan control for this system on arch linux using lm-sensors and fancontrol/pwmconfig.

Any suggestions on how to debug this further would be appreciated :)
Cheers

---

