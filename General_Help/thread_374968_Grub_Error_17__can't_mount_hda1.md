---
title: "Grub Error 17 / can't mount hda1"
date: 2007-03-03
forum: General Help
---

### Post by Alex99 on 2007-03-03
Hi,
when I reboot the szstem there's a message GRUB Error 17. I'm now trying to mount my partitions from a ubuntu 6.06 live CD, which doesn't work either.

If I run```
 fdisk-l 
```it yields:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  83  Linux
/dev/hda2             123        9729    77168227+   5  Extended
/dev/hda5             123         365     1951866   83  Linux
/dev/hda6             366        9729    75216298+  8e  Linux LVM
```

Unfortunately I can't check what my boot/grub/menu.lst says because I can't mount /boot.

if I enter
```
mkdir /hdrive
mount /dev/hda1 /hdrive
```

the result is
```
mount: you must specify the filesystem type 
```

I suspect that the filesystem type on hda1 is corrupt, and that's the reason I can't mount the partition and that the error 17 

In case it matters, this is my fstab:

```
##/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1##
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/vg00-root /         xfs     defaults,errors=remount-ro 0       1
/dev/mapper/vg00-home /home           xfs     defaults        0       2
/dev/mapper/vg00-tmp /tmp            xfs     defaults        0       2
/dev/mapper/vg00-usr /usr            xfs     defaults        0       2
/dev/mapper/vg00-usrlocal /usr/local      xfs     defaults        0       2
/dev/mapper/vg00-var /var            xfs     defaults        0       2
/dev/mapper/vg00-swap none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0   /media/floppy0/ vfat   rw,user,noauto   0   0 

```

---

### Post by webofunni on 2007-03-03
which are the other os's that you are using with ubuntu

---

### Post by Alex99 on 2007-03-04
I use only Ubuntu.

---

