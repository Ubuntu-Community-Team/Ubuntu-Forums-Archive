---
title: "put some code in startup"
date: 2008-03-07
forum: General Help
---

### Post by residentevil on 2008-03-07
I want to put some code to execute every time i boot my machine .
I want to put something like this

ifconfig eth0 192.168.0.1
mount -t ntfs-3g /dev/sda1 /media/sda1

So I want my Ip to be set and the second hdd to be mounted every time when i startup my pc .
sry for my bad English.

---

### Post by PinkFloyd102489 on 2008-03-07
Stick it in /etc/rc.local

---

### Post by bodhi.zazen on 2008-03-07
Actually you set the mount options in fstab

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

and to configure your static IP :

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

[http://www.ubuntuforums.org/showthread.php?&t=313282](http://www.ubuntuforums.org/showthread.php?&t=313282)


=========\

Noting "wrong" with putting those in /etc/rc.local, just thought I would show the standard approach

---

