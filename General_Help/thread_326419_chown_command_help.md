---
title: "chown command help"
date: 2006-12-27
forum: General Help
---

### Post by kolinab on 2006-12-27
Hi,

Like many others, I'm having a time with my external HDD. It mounts automagically, but the ext3 partition on it is owned by root. I tried to change it but . . . well you can see the terminal output. Maybe I'm not using chmod correctly? Oh, and I unmounted the drive before attempting said operation . . .

kolin@insp:~$ sudo fdisk -l
Password:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1958    15727603+  83  Linux
/dev/sda2            1959        9415    59898352+  83  Linux
/dev/sda3            9416        9546     1052257+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    5  Extended
/dev/sdb5               1       22409   180000229+  83  Linux
/dev/sdb6           22410       24321    15358108+   b  W95 FAT32
kolin@insp:~$ sudo chown kolin /dev/sdb5
kolin@insp:~$

---

### Post by kolinab on 2006-12-27
Additionally, I don't have a thing on the drive yet - I formatted it in GParted and could do so again with some kind of parameter if need be. But I've been using the graphical GParted 'cause I'm still learning the command line.

---

### Post by taurus on 2006-12-27
You cannot change owner of a partition; you can, however, change the owner of a mount point.  Therefore, if you mount /dev/sdb5 to /media/sdb5, then you can do something like

```
sudo chown -R kolin /mnt/sdb5
```

---

### Post by kolinab on 2006-12-27
Ok cool, that worked. It sticks, and still mounts automagically. I'm hoping I won't have permissions problems when I try to backup to this drive from a rescue cd. It surprised me that I wan't set up as owner when the drive was partitioned because it was me who did the partitioning. 

Well this works for now. Thanks!

---

### Post by taurus on 2006-12-27
Actually, everything outside $HOME is owned mostly by root!  So, kolin is only the owner of $HOME unless you change the ownership which you just did...  ;)

---

