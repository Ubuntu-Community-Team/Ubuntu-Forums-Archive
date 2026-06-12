---
title: "Auto mount/acess-NTFS disk at boot?"
date: 2008-05-13
forum: General Help
---

### Post by DeKosta on 2008-05-13
Hello people, how are you doing?

Im a linux newbie, i admitt that.
So on to my concern.. Now everytime i reebot and login to my Ubuntu account and start Deluge(Bittorrent client), i think its the same prob with every client.
So when i start Deluge i get some errors that there are not enough drive space for the files, etc. etc. (All the files are on another disk - "D"(NTFS disk) and Deluge doesn't seem to be able to access them after a reboot.)

The thing is as it is Now i have to browse to my "D"(NTFS disk) and accually browse Into it so i see the files on it - before i start up Deluge after a boot.

This is something i forget EVERY time so i have to re-check all the files in Deluge to get 'em goin' again. So enough said im pretty sick of it.
So, Linux-gurus... how do i solve this the easiest and less messy-way?

Thanks!

---

### Post by strabes on 2008-05-13
To begin, please paste the output of the following three commands in a terminal (Applications, Accesories, Terminal). The first command will prompt you for your password. When you enter it, characters will not appear but when you are done entering it simply hit enter. When you are done with all three commands paste their output in this thread.
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by Joeb454 on 2008-05-13
See the link at the bottom of my sig :) It should work just fine as long as you follow it

---

### Post by DeKosta on 2008-05-13
Allright here we go;

```
Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaebfa236

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3374    27101623+  83  Linux
/dev/sda2            3375        3593     1759117+  83  Linux
/dev/sda3            3594        3738     1164712+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4d5b4d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14596   117242338+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd513d513

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdc2            6375       30401   192996877+   7  HPFS/NTFS

```

**sudo blkid**
```
/dev/sda1: UUID="669e3785-2bc4-4481-8118-74b7afaa9671" TYPE="ext3" 
/dev/sda2: UUID="294dd9db-19ce-4062-8372-77d9cf9e60d4" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="1493a70f-381b-4ea6-be92-e6719316f04b" 
/dev/sdb1: UUID="9CFCB20AFCB1DF28" TYPE="ntfs" LABEL="Lagring 2" 
/dev/sdc1: UUID="72E8E44EE8E411E1" TYPE="ntfs" 
/dev/sdc2: UUID="5260CBB460CB9D5B" LABEL="Lagring 1" TYPE="ntfs" 

```

**cat /etc/fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=669e3785-2bc4-4481-8118-74b7afaa9671 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=294dd9db-19ce-4062-8372-77d9cf9e60d4 /home           ext3    relatime        0       2
# /dev/sda3
UUID=1493a70f-381b-4ea6-be92-e6719316f04b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Thats what i got from the commands you provided me with.
@**Joeb454**: Thanks mate, will check out the links too and see if i come up with a solution on my on hand also.

Allright i looked through your guide there and it was real easy and all but i came to a point where im not totally sure and i
**dont** want to risk scr***ng my disks up so i'll better ask you.

When i chose which disks to mount i just mark them, but that didn't do it, i had to give them names?
And i didn't dare to rename them... and when i clicked in the name twice it said something about invalid character.

---

