---
title: "SDCard Reader mismount conundrum"
date: 2014-08-14
forum: General Help
---

### Post by yodals45 on 2014-08-14
I'm using Ubuntu 12.04, and a Transcend RDP5 USB SDCard reader ( [http://www.transcendusa.com/Products/No-214](http://www.transcendusa.com/Products/No-214) ).

Can anyone tell me why Ubuntu mounts my 32gig SDcard as "/dev/sdb1" ?
I can't write to it either, seems it's busy or in use or something
It looks like this:

USER@COMPY:~$ sudo fdisk -l
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192    62552063    31271936    c  W95 FAT32 (LBA)
USER@COMPY:~$

I need this SDCard to mount as "mmcblk0", you know, as a memory card..  
as I can't use "cat /sys/block/$SDCARD/device/name" and a whole bunch of related commands on this weird thing.

Can anyone tell me how to get this thing to mount properly? Thanks!

---

