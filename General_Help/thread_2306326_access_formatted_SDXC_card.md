---
title: "access formatted SDXC card"
date: 2015-12-14
forum: General Help
---

### Post by geomcd1949 on 2015-12-14
Error mounting /dev/sdb1 at /media/george/478E-3F59: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/george/478E-3F59"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

I'm trying to access a Sandisk Ultra 64GB 80 MB/s Class10 SDXC card in Ubuntu 14.04 LTS. When I place it in the computer, Ubuntu recognizes that it is a 64GB volume, but I get this message: Unable to access "64 GB Volume",
 followed by the explanation above. 

This 64 GB Volume requires formatting by the JVC GY-HM150 camcorder in which it used. The camera properly records video and audio on the formatted card, and I can see and hear in the camera's preview screen.

Thanks for advice and guidance.

~George

---

### Post by Vladlenin5000 on 2015-12-14
The problem is with its proprietary file system - exFAT -, not with the card or Ubuntu.
This should give you the required support: [http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04](http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04)

---

### Post by geomcd1949 on 2015-12-14
Thank you, Vlad! Installing 
exfat-fuse and exfat-utils

solved the problem. Really appreciate it.

~George

---

