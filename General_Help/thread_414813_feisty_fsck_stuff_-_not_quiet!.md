---
title: "feisty fsck stuff - not quiet!"
date: 2007-04-20
forum: General Help
---

### Post by smurphs on 2007-04-20
Hi, I've installed feisty and so far it seems very good. 

However, when booting the splash screen turns to text and it takes a while to do all this fsck stuff. They seem to check out and I get to feisty no probs, but this never happened in edgy, so i'm wondering if i've got a problem. The fsck did fail first time round but has been ok since.

The grub entry is set to quiet, so I'm a bit concerned at the noisiness! Maybe I should move feisty to a different partition?

Any help greatly appreciated.

dyl.

---

### Post by mcduck on 2007-04-20
There could be something wrong with your fstab file. Could you post outputs of 'cat /etc/fstab' and 'sudo fdisk -l' here?

---

### Post by smurphs on 2007-04-20
blimey that was quick! I love these forums (fora?)

dyl@dyl-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b23b343e-4455-4d12-ae5c-ea19e22985d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=C47D-55E7  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=1b33d302-9af1-413e-86af-2cfa3709fea5 /media/hda3     ext3    defaults        0       2
# /dev/hda5
UUID=f033f81d-f057-417a-b50e-581663dc37d1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/floppy1  auto    rw,user,noauto  0       0


dyl@dyl-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3771    30290526    c  W95 FAT32 (LBA)
/dev/hda2            3772        8269    36130185   83  Linux
/dev/hda3            8270        9544    10241437+  83  Linux
/dev/hda4            9545        9729     1486012+   f  W95 Ext'd (LBA)
/dev/hda5            9545        9729     1485981   82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016    c  W95 FAT32 (LBA)

I'm sharing my swap disk between the 2 ubuntus. Is that ok?

---

### Post by mcduck on 2007-04-20
You could try changing the last number on the FAT partition's entry line in fstab from 1 to 0. That would disable fsck for the FAT partition, which might solve your problem.

```
# /dev/hda1
UUID=C47D-55E7 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 0
```

Just use 'gksudo gedit /etc/fstab' to open the file for editing as root.

Sharing same swap partition between many Linux installs is fine.

---

### Post by smurphs on 2007-04-20
that did the trick! thanks a million.

---

### Post by county_bg on 2007-04-23
I had the same problem since upgrading to feisty.
Correcting fstab, however, worked like a charm.

Thanks a bunch, mcduck.

P.S. I Love ubuntuforums... :-)

---

