---
title: "Every time I backup my sytem won't boot."
date: 2007-10-29
forum: General Help
---

### Post by thelocust on 2007-10-29
I tried using the Gparted live cd and made copies of my boot and root partitions. After backing them up I tried to restart my system and it freezes during startup. So I did a fresh install and tried to back up using dd ```
sudo dd bs=15M if=/dev/sda1 conv=sync,noerror | gzip -9 > /backup/boot/boot.img.gz
``` that I got and modified form [this thread]("http://ubuntuforums.org/showthread.php?t=581680"). and the same thing happened. So why can't I use dd. Any ideas thanks.

---

### Post by thelocust on 2007-10-30
No love?

---

### Post by thelocust on 2007-10-30
bump

---

### Post by thelocust on 2007-10-30
> **bhencetotozo said:**
> Sorri for interrupting people i dont mena to be rude, but please take your time to help me, a linux newbie.
 
i have linux ubuntu 7.10 x86 ..
CANNOT install the LINUX driver NOR beryl ... I need help.. I just started.
 
The motivation i have is that i sucessfully installed adobe flash plugin for firefox after reading on google for 8 hours...
 
i been reading for 8 days now and i cant figure out how toinstall NVIDIA driver..
 
Please read my thread [http://ubuntuforums.org/showthread.php?t=597969](http://ubuntuforums.org/showthread.php?t=597969)
and help me. Thank you very much people.
 
wtf?

---

### Post by init1 on 2007-11-03
> **thelocust said:**
> I tried using the Gparted live cd and made copies of my boot and root partitions. After backing them up I tried to restart my system and it freezes during startup. So I did a fresh install and tried to back up using dd ```
sudo dd bs=15M if=/dev/sda1 conv=sync,noerror | gzip -9 > /backup/boot/boot.img.gz
``` that I got and modified form [this thread]("http://ubuntuforums.org/showthread.php?t=581680"). and the same thing happened. So why can't I use dd. Any ideas thanks.
This doesn't seem like valid dd syntax. I've never used it quite like this. If you want to backup with dd, do a "dd if=/dev/yourpartitionhere of=/where/you/want/the/image.img". Obviously, you'll need to edit that command before you can use it. There may be a better way, but that should work. It will make a file that contains the exact contents of that partition.

---

