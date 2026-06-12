---
title: "df not reporting root filesystem - is'nt it strange?"
date: 2007-02-16
forum: General Help
---

### Post by john_brown_jr on 2007-02-16
Hello Ubuntu folks:

When I execute 'df -h', I don't see my root filesystem. I'm not that experienced with Ubuntu (this is my first week with it), so please guide me if i'm doing something stupid here.

sudo df -h
```

Filesystem            Size  Used Avail Use% Mounted on
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  104K  9.9M   2% /proc/bus/usb
udev                   10M  104K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/mapper/home       98G   84G   15G  86% /mnt/home
```

/etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=9cb348d6-fa2a-4547-9544-a353ca39b111 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
#UUID=847d5d89-c467-4e81-9ac1-9bb88b85e05b /media/hda1     ext3    defaults        0       2
# /dev/hda4
UUID=4cd66810-8b0b-441b-8fda-33daab3696f6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

sudo fdisk -l
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          13      104391   83  Linux
/dev/hda2   *          14        1580    12586927+  83  Linux
/dev/hda3            1840       14593   102446505   83  Linux
/dev/hda4            1581        1839     2080417+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

hda1 is boot partition for emergencies, currently not used
hda2 is partition with ubuntu
hda3 is encrypted volume
hda4 is swap partition

---

### Post by john_brown_jr on 2007-02-19
I managed to temporary fix it by removing /etc/mtab, and then symlinking /proc/mounts to it. However, I have no idea what caused it or how to fix it properly. Could it be that the process responsible for creating/updating my /etc/mtab somehow screwed up?

Any ideas?

---

