---
title: "[SOLVED] Xorg 15 to 25% CPU usage when idle"
date: 2008-01-07
forum: General Help
---

### Post by santaslittlehelper on 2008-01-07
Just before Xorg started to act up I installed nvclock and lm-sensors, I removed both again. Of cause I am not sure that either nvclock or lm-sensors had anything to do with Xorg's sudden CPU usage, but I am fairly sure it was the last thing I installed and before this all was fine.

ubuntu 7.10
AMD X2 5200
8800 GTS
NVIDIA-Linux-x86-169.04

Htop shows:
~25% CPU usage to /usr/bin/X :0 -br -audit 0 -auth /varlib/gd/:0.Xauth -nolisten tcp vt7

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_control_fan_speed_.28lm-sensors.29)
I followed the above howto.

[http://ubuntuforums.org/showthread.php?t=503119](http://ubuntuforums.org/showthread.php?t=503119)
From the above post I think that it might be related to lm-sensors because of some moduls stuff, just not sure at all.

If anyone got any suggestion how I might fix this I would appreciate it.

---

### Post by santaslittlehelper on 2008-01-07
It was late last night and I wanted to set lm-sensors up on ubuntu because I just had done so on arch and for the first time I noticed I had harddisks :D Which was real nice. 

Anyway what I forgot was that I also messed around with the BIOS and enabled "Cool'n'Quiet" just disabled it and all is fine again :D

Also got lm-sensors up and running with this howto.
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Sweet :D

---

