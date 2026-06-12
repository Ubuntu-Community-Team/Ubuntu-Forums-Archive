---
title: "error splicing file: No space left on device"
date: 2016-02-08
forum: General Help
---

### Post by tarzanofnazareth on 2016-02-08
Hi folks. Some help here would be really appreciated!!  I keep getting  'error splicing file: No space left on device'  when i try saving things in my Media file. i deleted a lot of files  (a good few gigs worth) to reduce space but the problem persists. I have been looking around and have seen similar problems without being able to understand or see solutions. But i think i know where the problem is - in the /dev/sdb1 . 

I have run the following commands and here outputs:  

```
adam@adam-P5K-VM:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1       74858656  41826284  29229700  59% /
udev             1019724         4   1019720   1% /dev
tmpfs             206084       980    205104   1% /run
none                5120         0      5120   0% /run/lock
none             1030412     37624    992788   4% /run/shm
/dev/sdc1       15252928     45032  15207896   1% /media/KINGSTON
/dev/sdb1      156288320 156288320         0 100% /media/Media
```


```
adam@adam-P5K-VM:~$ yum clean packages

The program 'yum' is currently not installed.  You can install it by typing:
sudo apt-get install yum
```

```
adam@adam-P5K-VM:~$ sudo fdisk -l
[sudo] password for adam: 


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093e92


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   152109055    76053504   83  Linux
/dev/sda2       152111102   156301311     2095105    5  Extended
/dev/sda5       152111104   156301311     2095104   82  Linux swap / Solaris


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10c610c5


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 15.6 GB, 15634300928 bytes
255 heads, 63 sectors/track, 1900 cylinders, total 30535744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          64    30535743    15267840    c  W95 FAT32 (LBA)
```

---

### Post by matt_symes on 2016-02-08
Hi

> /dev/sdb1 156288320 156288320 0 **100%** /media/Media

The above */media/Media* is a partition and it's that which is full up

Kind regards

---

### Post by tarzanofnazareth on 2016-02-08
so how do i un-fill it, as deleting many gigs of data doesnt do anything. It also went from 30% to full without me really adding any big files

---

### Post by matt_symes on 2016-02-08
Hi

> **tarzanofnazareth said:**
> so how do i un-fill it, as deleting many gigs of data doesnt do anything. It also went from 30% to full without me really adding any big files

How did you delete them ?

Did you just move them to 'trash' or 'rubbish' ?

If so, you'll want to empty the 'trash can' or 'rubbish bin'.

Silly question, you did delete files from that partition ?

BTW:

yum is the package manager for redhat and related releases. You don't need to install that on Ubuntu.

Kind regards

---

