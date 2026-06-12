---
title: "Mount 2nd Win drive"
date: 2007-11-26
forum: General Help
---

### Post by NJC on 2007-11-26
Using Ubuntu 7.10 and dual-boot Win98 on a 2nd HD. I recently added a 3rd HD (Win98 cloned drive) but it killed off the automount of 2nd Win HD. Here's Fstab entry 2nd Win HD: 
```
#/dev/sdb1       
UUID=1610-375D  /media/windows  vfat    user,iocharset=utf8,umask=000   0       0
```
I've used this without "user" too. But twice I reboot with 3rd drive installed and lose permissions to mount the 2nd drive, as I detailed here: [http://ubuntuforums.org/showthread.php?t=619933](http://ubuntuforums.org/showthread.php?t=619933) The third drive properly shows up as /dev/sdc1.
 
Bug? Operator-error? Feedback appreciated ... if it is a bug, I'll try and replicate it again and report.

---

