---
title: "Unable to read SD card"
date: 2015-06-11
forum: General Help
---

### Post by todaymueller on 2015-06-11
I have recently bought a new video camera and in order to use the slow motion facility I have started using a class 10 sandisk extreme 64G SD card. I was able to mount and download from a slower card but with this one I get the message ;

Unable to mount CAM_SD
Error mounting /dev/sdc1 at /media/john/CAM_SD: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdc1" "/media/john/CAM_SD"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

Is there anyway round this? I am running 14.04 LTS on a fairly old dell computer.

---

### Post by ajgreeny on 2015-06-11
You probably need to install **exfat-tools** and **exfat-utils** packages, which should allow Ubuntu to deal with the card.

Is exfat the filesystem that the video-camera makes when it formats the card, or is it what was on the card when you got it?  What filesystem does the video-camera normally use; ours is fat32 by default, not exfat.

---

### Post by todaymueller on 2015-06-11
Ha !
solved :p I pasted 
```
sudo apt-get update && sudo apt-get install exfat-fuse exfat-utils
```
into the terminal and hey presto problem solved.
Large SD cards are exfat.
Thanks for the help.

---

### Post by LastDino on 2015-06-11
> **todaymueller said:**
> Ha !
solved :p I pasted 
```
sudo apt-get update && sudo apt-get install exfat-fuse exfat-utils
```
into the terminal and hey presto problem solved.
Large SD cards are exfat.
Thanks for the help.
Fantastic!
Please mark the thread as ''solved'', it helps others to concentrate on threads which still need help. My post contains ''how to'' just in case.

---

