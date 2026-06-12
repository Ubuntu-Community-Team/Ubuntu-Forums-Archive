---
title: "CD Permissions"
date: 2007-02-21
forum: General Help
---

### Post by superdumbell on 2007-02-21
wierd problem, on my turbotax 2006 cd only the root user can read the cd, but I dont have this problem with any other cd I have, for some reason the permissions are set only for the root user

here is my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=d1e3c371-0db2-4a1a-a952-fea9290bda56 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=cb525727-7d7e-48f2-9c60-ae25b83a82a7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,user,defaults     0       0
/dev/hda1    /media/backup vfat  iocharset=utf8,umask=000  0    0
```

---

### Post by DagMan on 2007-02-21
to diagnose your problem a little better, see if this solves it until the next reboot
sudo chmod 660 /dev/hdc
or even 
sudo chmod 666 /dev/hdc

and if not see if this solves it
sudo gpasswd -a USERNAME cdrom
where USERNAME is your username

Edit: looking at this again and how it differs from my fstab enty, try using this as well and see if that makes a differance
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

