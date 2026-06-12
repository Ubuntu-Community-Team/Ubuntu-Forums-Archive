---
title: "[SOLVED] &amp;quot;You are not privileged to mount this volume&amp;quot;"
date: 2008-03-25
forum: General Help
---

### Post by kens8 on 2008-03-25
I just got a new hard drive to replace the two smaller ones I had in my system.  I installed XP, then installed Gusty.  During the Gusty install I created a large FAT32 partition to house music and videos I want to have available from both OSes.  Now I can't access the FAT32 partition.  I get the error message "You are not privileged to mount this volume".  If I can't figure this out soon, I'll just have to reformat that partition and hope that fixes it.

---

### Post by ibuclaw on 2008-03-25
copy and paste the output of these commands:
```

nano /etc/fstab

```
and
```

groups

```

Regards
Iain

---

### Post by sujoy on 2008-03-25
add yourself to the wheels group

---

### Post by kens8 on 2008-03-26
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4e79cce2-490b-4c83-a810-2cd02f4c0da8 /               ext3    defaults,erro$
# /dev/sda5
UUID=86072f49-23ec-495f-ab86-b0687042ff6a none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda3       /media/Media    vfat    default 0       0
```


```
keeslings adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
```

---

### Post by PmDematagoda on 2008-03-26
Can you please post the output of:-
```
sudo fdisk -l
```

---

### Post by kens8 on 2008-03-26
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x139a73fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4864    39070048+   7  HPFS/NTFS
/dev/sda2   *        4865       12562    61834185   83  Linux
/dev/sda3           12896       60801   384804945    b  W95 FAT32
/dev/sda4           12563       12895     2674822+   5  Extended
/dev/sda5           12563       12895     2674791   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 120.0 GB, 120033041920 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dd6ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241   83  Linux
```

---

### Post by PmDematagoda on 2008-03-26
Since sda2,3 and 5 are mounted by fstab, what partition are you trying to mount? sda1 or sdc1?

---

### Post by vanadium on 2008-03-26
For one thing, "default" is not a valid option in /etc/fstab. Change that to "defaults" first. Then save fstab and try remounting it:

sudo mount -a

There should not be any output. If there is, then post the output here: it will give a hint about what is wrong.

---

### Post by kens8 on 2008-03-26
PmDematagoga:  I was trying to mount sda3.  I entered it into /etc/fstab manually and it wouldn't mount.

vanadium:  Thank you!  What a difference a letter makes!  Works fine now, except that it's owned by root for some reason.  But that's easily dealt with.

---

