---
title: "strange error message (Ubuntu 6.10)"
date: 2007-04-10
forum: General Help
---

### Post by Willie G on 2007-04-10
After typing "sudo -i" to get temporary root priviledges
and opening nautilus, I found the following error message
in the terminal console


Volume monitoring will not work.
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
root@user-laptop:~# 


What is this supposed to mean?  I'm just opening
nautilus, not invoking any audio application.


Sound device:
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

installed packages
alsa base
alsa-oss
libesd-alsa0
libsdl1.2debian-alsa
libpt-plugins-alsa
oss-compat
alsa-utils

---

### Post by m.musashi on 2007-04-10
Try using
```
gksudo nautilus
```
instead. My understanding is that is the preferred way to run nautilus as root. It may or may not have anything to do with the errors, but it's possible they are caused by conflicting privileges.

---

