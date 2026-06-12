---
title: "External Drive Mounting Problems"
date: 2007-10-10
forum: General Help
---

### Post by aparigraha on 2007-10-10
I have a problem mounting two partitions from an external drive when booting. The drive is connected through USB. I have the partitions in /etc/fstab/ The drives are /dev/sdc1 and sdc2. 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c3ddb78e-5ddf-418a-9cbb-09bf14b7e73b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=3f81d4a8-fae0-4f31-9fb2-9853376767be /home           ext3    defaults        0       2
# /dev/sdb1
UUID=3180f3fa-8946-46cf-b923-6e39803d6e76 /media/sdb1     ext3    defaults     0      1
# /dev/sda2
UUID=e51e65a0-3867-4dc7-b82f-81819d8db357 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sdc1
UUID=3be15949-c89d-4a62-a120-cc3138d2053f /media/Extern   ext3   defaults     0      1
#/dev/sdc2
UUID=4705-87CD /media/Backup   vfat   user,fmask=0111,dmask=0000   0   0

```

I have tried replacing UUID with /dev/sdc1/ (and /sdc2) but no difference.
When booting I reach a shell which gives me something like this:

```
fsck died with exit 8 status.
File system check failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
```

And then an error message at the bottom of the screen which mentions a problem with USB3. After I hit the mentioned CONTROL-D the system boots up nicely and both partitions are mounted automatically without a problem. I have tried switching USB-ports... but no difference. Same booting problems. What could be the problem here? Permissions maybe? Or something with the mounting options in fstab perhaps? 

sudo fdisk -l gives me this:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1338      979965   82  Linux swap / Solaris
/dev/sda3            1339       24321   184610947+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       41345   312568168+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58247   467868996   83  Linux
/dev/sdc2           58248       60801    20515005    b  W95 FAT32

```

Need help here! How can I get it to mount on boot without error messages and having to press CTRL-D?

---

### Post by aparigraha on 2007-10-12
a little bump. please share your ideas. what do i have to do here?

---

### Post by aparigraha on 2007-10-15
anyone?

---

