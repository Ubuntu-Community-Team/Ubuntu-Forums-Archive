---
title: "Grub doesn't recognize Windows"
date: 2007-07-04
forum: General Help
---

### Post by weissnich on 2007-07-04
I have first installed Windows on partition 7 on my hard drive, then I installed Ubuntu on partition 1.
Grub doesn't recognize Windows, it just gives me this error:
Error 13: Invalid or unsupported executable format
Is this a Grub problem?

---

### Post by Computer-Slave on 2007-07-04
I can't tell u the solution to this problem but i cantell u that this is not a GRUB problem.

---

### Post by weissnich on 2007-07-04
Maybe it happens because Windows is on partition sda7 ?
How can I find out what is wrong, I really cannot delete the partition,
I have to somehow make Windows bootable again.

---

### Post by jespdj on 2007-07-04
Can you mount that Windows partition when you're in Linux?
Is the Windows partition in your /etc/fstab?

---

### Post by weissnich on 2007-07-04
Yes, the Windows partitions are mountable.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e5d08cbe-ab71-4114-9ecb-a725e0bf4b5a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=a4d6970c-a74c-4841-899e-ad0f3a76d9c7 /home           ext3    defaults        0       2
# /dev/sda7
UUID=4C44876C1E578DD4 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=43BADE482D113D61 /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=173B2AA52A90DB61 /media/sda9     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=c0c30c2f-8160-4b9d-b118-576cd959ca97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

sda7 is the Windows OS.

---

### Post by Pimpn8ezy on 2007-07-10
Can we see the contents of /boot/grub/menu.lst and the output of sudo fdisk -l?

---

