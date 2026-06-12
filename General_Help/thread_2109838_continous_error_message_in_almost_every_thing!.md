---
title: "continous error message in almost every thing!"
date: 2013-01-28
forum: General Help
---

### Post by Linuxour on 2013-01-28
Hello,

Every time i open Dolphin File Manger or any application this message appears


" Configuration file "/home/linux4ever/.kde/share/config/(Name of any applicaion )" not writable.
Please contact your system administrator. "


When i tried to open Dolphin the same message appears but it was opened but when opening any device this message appears

" The process for the file protocol died unexpectedly. "


What should i do ?

---

### Post by ajgreeny on 2013-01-28
This sounds like a permissions error to me so try making the ownership and permissions of the .kde folder mentioned in the error correct using the commands in terminal (konsole) ```
sudo chown -R linux4ever:linux4ever /home/linux4ever/.kde
```to make sure it's it yours, and then ```
chmod -R 755 /home/linux4ever/.kde
```
I wonder if other folders in your home also have incorrect permissions.  If you get other problems, come back again, or as a cover-all solution run ```
sudo chown -R linux4ever:linux4ever /home/linux4ever
```then ```
chmod -R 755 /home/linux4ever
```which will make sure everything in your home has correct ownership and permissions.

---

### Post by Linuxour on 2013-01-28
Thank you ... I did as you said and restarted the computer but

The following appeared and i couldn't log in .

" Errors were found while checking the disk driver for /. 

Press F to attempt to fix the errors, I to ignore , S to skip mounting or M for Manual recovery "

I pressed "I" then i had a black screen with this 

===
Ubuntu 12.10 Linux4Ever

Login:
===

I entered my username and pass but it was just like a terminal

I tried "S" too , but the same happened .

---

### Post by ajgreeny on 2013-01-29
OK, I think you may have a filesystem error, or even a hard disk failing, so try booting to a live CD or USB then running ```
sudo fdisk -l
```and report back here the output in code tags (the # in toolbar above the reply box).

It will also be worth running ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition, and if you have a separate /home partition run it on that as well.

---

### Post by Linuxour on 2013-01-29
Excuse me, but do you mean by "  a hard disk failing " that something is wrong with it and i may have to buy a new one ?

```

kubuntu@kubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c530c52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280   83  Linux
/dev/sda2        62918654   976773061   456927204    f  W95 Ext'd (LBA)
/dev/sda5       286712118   737270711   225279297    7  HPFS/NTFS/exFAT
/dev/sda6       737271108   976773061   119750977    7  HPFS/NTFS/exFAT
/dev/sda7        62918656   246674514    91877929+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 8019 MB, 8019509248 bytes
19 heads, 24 sectors/track, 34348 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x662b31d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     1952343      976140   17  Hidden HPFS/NTFS
```



```


kubuntu@kubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

```

Note: I had this problem two times before and had to reinstall the system.

---

### Post by SeijiSensei on 2013-01-29
> **Linuxour said:**
> 
```

kubuntu@kubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

```

Just to make sure, you booted from the CD or a USB device, then chose "Try Kubuntu" when offered the opportunity?

By default, that method should not mount any of the partitions on /dev/sda at all.  Right after you get the desktop, and before doing anything else, open a terminal (Konsole) and run e2fsck.  If you still get the "is mounted" problem, then run "mount" at the command prompt.  Where is /dev/sda1 mounted?  Try "cd /; umount -f /dev/sda1"?  If that doesn't return an error, run e2fsck again.

---

### Post by Linuxour on 2013-01-29
Thank you .. after i had typed it this appeared


```
kubuntu@kubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.42.5 (29-Jul-2012)
Superblock last write time is in the future.
        (by less than a day, probably due to the hardware clock being incorrectly set).  Fix<y>? 

```

should i type "y" ?

---

### Post by SeijiSensei on 2013-01-29
Yes.  In general, you should just say yes to everything.  There is even a "-y" option to e2fsck which says yes for you automatically.  I don't use that very often, though, as I typically experience only a few errors.  I'd rather see what is being asked, though largely more for curiosity than any technical reason.

---

### Post by Linuxour on 2013-01-29
Thank god the problem was solved.

Ajgreeny and SeijiSensei thank you very much for your efforts.

---

