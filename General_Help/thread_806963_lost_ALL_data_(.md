---
title: "lost ALL data :("
date: 2008-05-25
forum: General Help
---

### Post by fallstoofast on 2008-05-25
On fedora 9....

I have 3 external harddrives with EVERYTHING
but in the process of installing fedora, I think fedora formatted the hard drives and encrypted them
(I only told it to format the main hard drive)
l 
Now windows can't even read it, and fedora is saying it's encrypted.

I enter the password and the drive disappear. Should I try running spinrite? I really can't lose all the stuff.......


spinrite doesn't even recognize the drives... is this lost for ever? I have all my family pictures in there too and my mom'll kill me

---

### Post by cdtech on 2008-05-25
Can you boot into any Linux OS?

---

### Post by fallstoofast on 2008-05-25
I'm on fedora 9 right now but it's reading the drives as "encrypted drives" and when I enter my password they disappear. And I think the installer formatted them?....

---

### Post by cdtech on 2008-05-25
What do you get with fdisk -l ?

---

### Post by fallstoofast on 2008-05-25
It says command not found..

---

### Post by fallstoofast on 2008-05-25
did it in root


Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        4864    38869267+  8e  Linux LVM

Disk /dev/dm-0: 37.6 GB, 37681627136 bytes
255 heads, 63 sectors/track, 4581 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2080 MB, 2080374784 bytes
255 heads, 63 sectors/track, 252 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30307800

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020a72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   8e  Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002149d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001   8e  Linux LVM

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f95c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001   8e  Linux LVM

Disk /dev/dm-4: 500.1 GB, 500104688640 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-4 doesn't contain a valid partition table

Disk /dev/dm-2: 250.0 GB, 250056176640 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 500.1 GB, 500104688640 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table
[root@localhost ~]# fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        4864    38869267+  8e  Linux LVM

Disk /dev/dm-0: 37.6 GB, 37681627136 bytes
255 heads, 63 sectors/track, 4581 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2080 MB, 2080374784 bytes
255 heads, 63 sectors/track, 252 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30307800

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020a72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   8e  Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002149d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001   8e  Linux LVM

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001f95c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001   8e  Linux LVM

Disk /dev/dm-4: 500.1 GB, 500104688640 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-4 doesn't contain a valid partition table

Disk /dev/dm-2: 250.0 GB, 250056176640 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 500.1 GB, 500104688640 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table

---

### Post by cdtech on 2008-05-25
Use full path: /sbin/fdisk, or add :/sbin: to your $PATH var

---

### Post by cdtech on 2008-05-25
what do you get running pvm ?

---

### Post by fallstoofast on 2008-05-25
umm... sorry, but I don't know what that is

and thanks for all your help

ah, I hope I didn't lose everything

---

### Post by cdtech on 2008-05-25
You are running LVM and mounting the drives are different than with standard. I have to go for now, but search LVM partition and that should help you. I dont think you've lost anything.

good luck......

---

