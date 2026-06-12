---
title: "Mounting windows partition"
date: 2006-12-03
forum: General Help
---

### Post by iNick92 on 2006-12-03
Im trying to mount my windows partition in ubuntu 6.10. Im using this guide: [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows) Except i cant figure out which one is my windows partition when i edit the fstab 
```
sudo nano /etc/fstab
``` 

here is my ```
sudo fdisk -l
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        3579    18506880   83  Linux
/dev/hda3            3580        3648      554242+   5  Extended
/dev/hda5            3580        3648      554211   82  Linux swap / Solaris

and here is the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=007b6fd8-e121-4796-b4e0-fc7262876fcf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f5114b2d-9b2d-4b78-97ca-bd2f6a3296c9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2006-12-03
/dev/hda1 is your Windows partition!!!

---

### Post by iNick92 on 2006-12-03
I know that! but i cant tell which on is /dev/hda1 in fstab!

---

### Post by taurus on 2006-12-03
It's not in there.  You need to edit and add an entry for it!!!

---

### Post by iNick92 on 2006-12-03
ohhhhhh that makes more sence, thank you.

---

