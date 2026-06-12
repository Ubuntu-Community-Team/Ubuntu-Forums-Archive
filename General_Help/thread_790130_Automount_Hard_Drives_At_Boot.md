---
title: "Automount Hard Drives At Boot"
date: 2008-05-11
forum: General Help
---

### Post by linuxsudo on 2008-05-11
I would like to be able to Automatically Mount my Hard Drives when my system boots up. I have 2 drives which I would like to automount. 

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a8f74a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14024   112640000    7  HPFS/NTFS
/dev/sdb2           14025       19457    43640572+   5  Extended
/dev/sdb5           14025       19229    41809131   83  Linux
/dev/sdb6           19230       19457     1831378+  82  Linux swap / Solaris

```

Anyway the Drives which I would to Mount on Bootup are /dev/sda1 & /dev/sdb1. I can access these drives on the Places Menu currently, however I have to enter my password to access them. After this when I reboot they are not mounted and I have to do the same again, go to places, enter password and then it will mount. Can I set it so they are already mounted on boot?

---

### Post by Kevbert on 2008-05-11
You need to edit your fstab file.  This can be found in the /etc directory.
Info on how to do this is here: [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by linuxsudo on 2008-05-12
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=fbe78953-8243-4ada-84b8-b8b3fb649f5d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=e6d152aa-eef6-4026-949b-b7ad93128344 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

I don't understand how I'm going to get that to work, I've not managed to so far. Anyway that above is the contents of my fstab file. I know that /dev/sbd1 mounts at /media/Storage.

---

