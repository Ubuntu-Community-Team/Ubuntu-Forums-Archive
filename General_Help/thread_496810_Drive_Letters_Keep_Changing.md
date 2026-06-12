---
title: "Drive Letters Keep Changing"
date: 2007-07-09
forum: General Help
---

### Post by narehart on 2007-07-09
Hi I have a IDE and SATA hard drive.  The assignment letters for these drives keep changing randomly.  For instance the IDE with my linux and windows os will be /dev/sda then i reboot and it's become sdb and is unable to mount. Any ideas?

---

### Post by marsbt on 2007-07-09
Look into using UUID for your devices. With UUID you can fix which UUID (and hence device) gets which label when it is mounted.

[this article](http://www.debian-administration.org/articles/522) might help.

---

### Post by narehart on 2007-07-09
Well when i try to assign a UUID i get the error: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

---

### Post by jimbob on 2007-07-09
Use the command *[COLOR="Blue"]blkid[/COLOR]* to determine the UUID's of all drive partitions on your system.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by narehart on 2007-07-09
I tried that.  Only three of the partitions have UUIDs and I have seven total.

---

### Post by jimbob on 2007-07-09
Please post the output of *[COLOR="Blue"]sudo fdisk -l[/COLOR]*
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by narehart on 2007-07-09
I will as soon as I get home from school.  I appreciate you taking the time to help me.

---

### Post by narehart on 2007-07-09
here it is:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4864    39070048+   b  W95 FAT32
/dev/sda2            4865       17632   102558960   83  Linux
/dev/sda3           17633       30401   102566992+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2295    18434556    7  HPFS/NTFS
/dev/sdb2            2296        4753    19743885   83  Linux
/dev/sdb3            4754        4866      907672+   5  Extended
/dev/sdb5            4754        4866      907641   82  Linux swap / Solaris
```

---

### Post by narehart on 2007-07-09
well i finally fixed this problem.  i was able to rename the partitions in windows.  i downloaded a program that gave me rw access to my linux partitions and then just right clicked and renamed.  im not dissing linux but why isn't it like that in ubuntu. ah well just happy it works now!

---

