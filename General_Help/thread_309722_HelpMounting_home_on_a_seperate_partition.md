---
title: "Help:Mounting /home on a seperate partition"
date: 2006-11-30
forum: General Help
---

### Post by vikrant_me on 2006-11-30
I have created a seperate vfat partition of 1gb to mount /home on last time i tried editing fstab things went wrong so i would appreciate some help on mounting my /home on /dev/sda5 below is my sudo fdisk -l :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1700    13655218+  83  Linux
/dev/sda2            1829        2481     5245222+   c  W95 FAT32 (LBA)
/dev/sda3            2482        9729    58219560    f  W95 Ext'd (LBA)
/dev/sda4            1701        1828     1028160   82  Linux swap / Solaris
/dev/sda5            2482        3787    10490413+   b  W95 FAT32
/dev/sda6            3788        9729    47729083+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sdb2            2678        9728    56637157+   f  W95 Ext'd (LBA)
/dev/sdb5            2678        9728    56637126    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3189    25615611    7  HPFS/NTFS
/dev/sdc2            3190        9729    52532550    f  W95 Ext'd (LBA)
/dev/sdc5            3190        9729    52532518+   7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sdd2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sdd5            2551        5161    20972826    b  W95 FAT32
/dev/sdd6            5162        7772    20972826    b  W95 FAT32
/dev/sdd7            7773        9729    15719571    b  W95 FAT32

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4864    39070048+   c  W95 FAT32 (LBA)


and here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /media/media    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdd1       /media/sdd1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdd5       /media/sdd5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdd6       /media/sdd6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdd7       /media/sdd7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

                 I am aware that i have to just make a simple entry for /home /dev/sda5 /home vfat but thats all i know i am clueless about the options,dump,pass i am looking to give full rwx acess to the folder to all users.

Thanks.

---

### Post by aysiu on 2006-11-30
You shouldn't use FAT for a /home partition. Make it Ext3 instead. This will help you:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by binselam on 2006-11-30
Another option is to mount a directory under your home directory(not as your home directory).

---

### Post by vikrant_me on 2006-11-30
> **binselam said:**
> Another option is to mount a directory under your home directory(not as your home directory).

Huh i didnt get tht!

---

### Post by vikrant_me on 2006-11-30
> **aysiu said:**
> You shouldn't use FAT for a /home partition. Make it Ext3 instead. This will help you:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Why not?

---

### Post by aysiu on 2006-11-30
> **vikrant_me said:**
> Why not?
FAT32 doesn't support permissions, and permissions are the core of how Linux operates, particularly in the home directory. For example, [if your /home/username/.dmrc file isn't 644 (read/write for owner, nothing for everyone else), then you may not be able to log in](http://ubuntuforums.org/showthread.php?t=287609).

Trust me--you do not want your /home partition as FAT32 or FAT16. If you need to share files with Windows, use [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by vikrant_me on 2006-11-30
> **aysiu said:**
> FAT32 doesn't support permissions, and permissions are the core of how Linux operates, particularly in the home directory. For example, [if your /home/username/.dmrc file isn't 644 (read/write for owner, nothing for everyone else), then you may not be able to log in](http://ubuntuforums.org/showthread.php?t=287609).

Trust me--you do not want your /home partition as FAT32 or FAT16. If you need to share files with Windows, use [http://www.fs-driver.org](http://www.fs-driver.org)

Aaah makes a lotta sense! thanks :)

---

### Post by binselam on 2006-12-01
What I mean is that you can mount the new drive on a common mount location such as /mnt/fatdrive. Than, you can creat a link from your ~home to that location.
I would not suggest you to use the new linked location as your home  directory due to security issues.

---

### Post by drowner on 2007-05-30
Mega bump

Currently doing this, thanks psychocats (aysiu, isnt it?)

Oh, but before i do, i wonder if someone could tell me what this command means (i know all the rest):

```

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

and why it is so important?

from [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

