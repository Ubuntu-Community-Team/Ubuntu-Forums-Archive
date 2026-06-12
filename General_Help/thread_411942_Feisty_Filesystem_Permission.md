---
title: "Feisty Filesystem Permission"
date: 2007-04-17
forum: General Help
---

### Post by Temis on 2007-04-17
When I right click the Filesystem icon and the Properties - Permission   its says owner: unknown.
How can  I change this?

---

### Post by taurus on 2007-04-17
What partition is it?  Run it from a terminal for a better output.

---

### Post by Temis on 2007-04-17
Thank you for your reply. Sorry do not know how to do it.  What I do:  click Places - Computer - right click Filesystem icon - Properties -Permissions     Owner: unknown.  I would like to assign owner to the Filesystem.

---

### Post by earobinson on 2007-04-17
whats the name of the filesystem, in the terminal type ```
cat /etc/fstab
``` and cut and paste the output

---

### Post by Temis on 2007-04-17
This is the Terminal out put:
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=465af0f1-e3f0-4fdd-9287-513d0bf71992 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=20bda500-736e-48ae-8695-afb36d2b6b03 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0

---

### Post by taurus on 2007-04-17
Make sure you add another 0 at the end of the last entry, /dev/hdb1, in /etc/fstab

```
gksudo gedit /etc/fstab
```

```
/dev/hdb1 /media/windows vfat iocharset=utf8,umask=000 0 **0**
```
Also, what's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Temis on 2007-04-17
sudo fdisk -l  gives this result

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3465    27832581    c  W95 FAT32 (LBA)
/dev/sda2            3466        4803    10747485   83  Linux
/dev/sda3            4804        4865      498015    5  Extended
/dev/sda5            4804        4865      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9964    80035798+   7  HPFS/NTFS

---

### Post by Temis on 2007-04-18
Followup to my problem:
When I go Places - Computer  Output is Floppy Drive, CD_ROM, CD_RW/DVD, 26.5 GB Volume, 76.3 GB
Volume, Filesystem   in all cases the owner is unknown.
Bigger problem for me is that I cannot search files in the Filesystem.
When I click Places - Search for files I have only these options:
1. Home folder
2. Desktop
3 dev (I have no clue what this is)
4. Floppy drive
5. 26.5 GB Volume
6. 76.3 GB Volume 
but no Filesystem????
Appreciate any advise.

---

### Post by Temis on 2007-04-18
Well the whole problem started after I upgraded to feisty few days ago.

---

