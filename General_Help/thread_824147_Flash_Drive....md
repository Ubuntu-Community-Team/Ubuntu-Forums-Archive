---
title: "Flash Drive..."
date: 2008-06-09
forum: General Help
---

### Post by new_at_linux on 2008-06-09
Hello,

Recently I tried installing Ubuntu to my flash drive.  After several frustrating HOURS of trying to get it to work, I pretty much gave it up.  Unfortunately, in the process of installation Ubuntu did something to my drive... I think it partitioned it?  When I put it into a computer, two drives come up, one is 3.7 GB and the other is 3.8 GB.  My flash drive is only 4 GB.

Does anyone know what's going on?  And how I can fix it?

Thank you in advance!

---

### Post by new_at_linux on 2008-06-11
Bump... can anyone help?  The computers at my school can't read my usb anymore because of this...

Also, it changed.  Now it's a 760MB FAT16 partition and a 3.8 GB partition which has no type(?).

Edit (again): For some reason I can access /media/disk (which is the 3.8 GB partition) WITHOUT putting in my flash drive.  Now I'm *really* confused.

---

### Post by spiritfox on 2008-06-11
try downloading the gparted livecd from gparted.sourceforge.net and using that in any random computer to look at the partition tables for the drive. You can also reformat and change partitions from this livecd.

---

### Post by new_at_linux on 2008-06-11
Thanks for the response, I'll try that.

---

### Post by new_at_linux on 2008-06-11
This is what I have learned:
My 3.8 GB partition is actually not on my flash drive at all, but on the computer.  It is under /dev/sdb, whereas my 760 MB partition is under /dev/sdf and is actually on the flash drive.  Somehow my 4GB flash drive was turned into a <1GB drive... under GParted I can only view sda and sdb drives.

Help? It kinda hurts a little to lose 3.3GB off a flash drive just because you wanted a liveUSB ubuntu... :confused:

---

### Post by simonasambler on 2008-06-11
It si quite weird that 1 physically drive /you usb key/ shows under sdb and other partition of the same disk is under sdf, are you sure ? Try type in console 
```
sudo fdisk -l
```
than find what is your usb key /a think it is sdb/
But when you are in Gparted select your sdb device it show only 750 mb that is because other space is unlocated, to fix it delete  750 mb /right click and delete/ partition  an click new and format fat32 filesystem, it shoul fix it.

---

### Post by new_at_linux on 2008-06-11
OK the result of that command is:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       15203   122061870    7  HPFS/NTFS
/dev/sda3           18998       19452     3654787+   b  W95 FAT32
/dev/sda4           15204       18997    30475305    5  Extended
/dev/sda5           15204       18850    29294496   83  Linux
/dev/sda6           18851       18997     1180746   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4036 MB, 4036492800 bytes
125 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x000c3012

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1017     3940844    6  FAT16


I booted into the LiveCD (Hardy Heron), put in my USB drive, and somehow my 700MB flash drive turned into a 4GB flash drive... I don't know why it suddenly switched, but my 3.7GB partition is still there too (with a mountpoint of /media/disk, even though the USB doesn't need to be in for me to mount it)... I really have no idea what's going on.  I'm going to reboot into Ubuntu (not LiveCD) and see if my drive is recognized as 4GB.

GParted wouldn't let me delete the 3.7GB partition, it had the "keys" symbol next to it.

EDIT: Yeah, linux recognizes my USB as a 4GB now.

---

### Post by Habbit on 2008-06-11
> **new_at_linux said:**
> GParted wouldn't let me delete the 3.7GB partition, it had the "keys" symbol next to it.

The "locked" symbol means the partition is in use, most probably mounted. Check if it is and unmount it if required. Working with GParted becomes difficult sometimes because making it "re-examine" the drives trigger HAL events which mount nearly all the partitions without notifying GParted - annoying.

---

### Post by new_at_linux on 2008-06-11
> **Habbit said:**
> The "locked" symbol means the partition is in use, most probably mounted. Check if it is and unmount it if required. Working with GParted becomes difficult sometimes because making it "re-examine" the drives trigger HAL events which mount nearly all the partitions without notifying GParted - annoying.

When I unmounted it, and refreshed the drives, GParted didn't show the partition anymore.  Now *that's* annoying.

---

