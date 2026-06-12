---
title: "NTFS Automount?"
date: 2007-02-20
forum: General Help
---

### Post by sprucio on 2007-02-20
I just installed a fresh copy of Ubuntu and for some reason, my NTFS partition is always automounted and displayed on my desktop.

Upon checking /etc/fstab, I don't see any auto options. Furthermore, I've disabled this entry totally from this file.

Can anyone help me as to why this is happening.

---

### Post by sprucio on 2007-03-02
Is anyone having the same issue?

One thing I forgot to add is that I have a RAID card installed here. I doubt it makes any difference but I just wanted to know if I can find the solution to this problem.

---

### Post by taurus on 2007-03-02
Can you post your /etc/fstab here?

```
cat /etc/fstab
```
And 

```
sudo fdisk -l
```

---

### Post by sprucio on 2007-03-11
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1f033176-8bfe-4866-9463-58aae5972ed5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=F2482A83482A46A7 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=50dc0a82-3c56-4b00-a753-c4df9d4bfcd1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

```
Disk /dev/sda: 319.9 GB, 319996035072 bytes
255 heads, 63 sectors/track, 38903 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528        9017    20000925   83  Linux
/dev/sda3            9018        9139      979965   82  Linux swap / Solaris
/dev/sda4            9140       38903   239079330    b  W95 FAT32
```

---

### Post by taurus on 2007-03-11
```
sudo rmdir /media/sda1
```

---

### Post by sprucio on 2007-03-25
There is no directory "sda1."

Does Ubuntu somehow scan for all partitions and then auto mount?

---

### Post by taurus on 2007-03-25
What's the output of this command from a terminal?

```
df -h
```

---

