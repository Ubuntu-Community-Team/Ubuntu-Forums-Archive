---
title: "Unable to mount 64G sd card"
date: 2018-12-01
forum: General Help
---

### Post by asb3 on 2018-12-01
When I try to mount a 64GB sd card, I get the following dialog box:

Unable to access &#8220;63 GB Volume&#8221;
Error mounting /dev/sde1 at /media/asb/0150-4440: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sde1" "/media/asb/0150-4440"' exited with non-zero exit status 1:
stdout: `FUSE exfat 1.2.3
'
stderr: `ERROR: unknown entry type 0x80.
'

The card works in the camera
I successfully mounted it in the past.
I can mount it on my wife's mac.

Any ideas?

---

### Post by ajgreeny on 2018-12-01
The error shows that the card has an exfat formatted partition.
You need to install the **exfat-fuse** and **exfat-utils** packages and the card should then mount as it used to.
```
sudo apt install exfat-fuse exfat-utils
``` will do it.

---

### Post by asb3 on 2018-12-01
exfat-fuse and exfat-utils were already installed:

asb@cavu> sudo apt install exfat-fuse exfat-utils
[sudo] password for asb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
exfat-fuse is already the newest version (1.2.3-1).
exfat-utils is already the newest version (1.2.3-1).
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

---

