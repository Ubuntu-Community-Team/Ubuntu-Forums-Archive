---
title: "Trying to mount W2K harddrive."
date: 2007-01-06
forum: General Help
---

### Post by ubdai on 2007-01-06
Trying to mount a w2k hardrive so as to move some files off it.
Have followed various thread and have done the follwoing

made a folder called /windows/hdd1

Have the following info
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9567    76846896   83  Linux
/dev/sda2            9568        9729     1301265    5  Extended
/dev/sda5            9568        9729     1301233+  82  Linux swap / Solaris

Disk /dev/hdd: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2434    19551073+   7  HPFS/NTFS
/dev/hdd2            2435        4867    19543072+   f  W95 Ext'd (LBA)
/dev/hdd5            2435        4833    19269936    7  HPFS/NTFS
/dev/hdd6            4834        4867      273073+   6  FAT16

Edited the fstab to 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b68e2086-6ec6-4b32-b3cf-0d19c56b4313 /               ext3    defaul$
# /dev/sda5
UUID=038bcf59-cb09-4dc4-90da-229377fbf65d none            swap    sw    $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1 /windows/hdd1 ntfs defaults,nls=utf8,unmask=007,gid46 0 0

Added the last line above.

Then tried to mount using 

sudo mount -a

and got 

mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any help would be appreciated.

ubdai:???:

---

### Post by kidders on 2007-01-06
Hi there,

There are typos in your mount options. Given that the error message is so amazingly vague, it's possible that correcting them could solve your problem ... but then again, it might not. Let us know!

> /dev/hdd1 /windows/hdd1 ntfs defaults,nls=utf8,unmask=007,gid46 0 0
[LIST]
[*]Change "unmask" to "umask".
[*]Change "gid46" to "gid=46".
[/LIST]

---

### Post by ubdai on 2007-01-06
SUCCESS - It worked.

Thanks:D

---

### Post by kidders on 2007-01-06
No problem. :-)
mount's man page has lots more information about the various mount options you can use in /etc/fstab, in case you ever need it.

---

