---
title: "ubuntu 7.10 can't see hebrew in cdrom disk folders"
date: 2008-01-11
forum: General Help
---

### Post by n00ne on 2008-01-11
Hi I just installed ubuntu a few days ago.

hebrew seems to be working fine , with no problems in nautilus and in the terminal, and even from my usb drive fat partition.

but I've just now tryed to copy stuff from some cds I have and all the hebrew is being desplayed as question marks (??? ??) inside the cd folders.

I tried to look around but couldn't really find any help on the subject.

the cd has joliet file system and was burned thru winXP 
and I'm using gnome

10x yoni

---

### Post by n00ne on 2008-01-12
Solved it.

added the following parameters to /etc/fstab cdrom line
iocharset=utf8


```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,iocharset=utf8,exec 0       0
```

---

