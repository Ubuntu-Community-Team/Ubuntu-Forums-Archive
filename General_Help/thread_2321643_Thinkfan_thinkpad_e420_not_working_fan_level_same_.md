---
title: "Thinkfan thinkpad e420 not working fan level same as on startup"
date: 2016-04-23
forum: General Help
---

### Post by miroslav9 on 2016-04-23
Hey,


I can't get my fan working properly on thinkpad edge e420. What it does that at startup it sets fan speed as is current temp of laptop and stays on that speed until restarted. So I can start laptop heat it up and restart and then use it for rest of the day but it is dangerous and annoying approach. I have followed this thread [http://ubuntuforums.org/showthread.php?t=1749186&page=1](http://ubuntuforums.org/showthread.php?t=1749186&page=1) and severel others forums to no avail. 
 Here everything important from my /etc/thinkfan.conf 

tp_fan /proc/acpi/ibm/fan

#tp_thermal /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/hwmon/hwmon1/temp1_input
hwmon /sys/devices/virtual/hwmon/hwmon0/temp1_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon2/temp3_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon2/temp1_input
hwmon /sys/devices/platform/coretemp.0/hwmon/hwmon2/temp2_input



(0, 0,  42)
(1, 40, 47)
(2, 45, 52)
(3, 50, 57)
(4, 55, 62)
(5, 60, 67)
(6, 65, 72)
(7, 70, 77)
(127,   75, 32767)

also one sensors that I found using find /sys/devices -type f -name "temp*_input" doesn't seems to be working with thinkfan it is the one commented(one with # and yes I have tried hwmon option).
I am using Ubuntu 15.10 but I had same problem with 15.04

If I start thinkfan using -n option levels change but speed doesn't. 
Whatever I do I cant get fan to work any ideas ? thanks
works fine on windows btw.

---

