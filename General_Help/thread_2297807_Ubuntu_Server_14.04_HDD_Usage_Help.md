---
title: "Ubuntu Server 14.04 HDD Usage Help"
date: 2015-10-06
forum: General Help
---

### Post by lee42 on 2015-10-06
Hi all

Just recently installed server 14.04 but the hard drive space is massive at 70odd GB

Server is running with 16GB of memory if thats something to do with it


Filesystem      1K-blocks       Used  Available Use% Mounted on
/dev/sdg1       106460232   76340212   24689032  76% /
none                    4          0          4   0% /sys/fs/cgroup
udev              8184568         12    8184556   1% /dev
tmpfs             1639064       1764    1637300   1% /run
none                 5120          0       5120   0% /run/lock
none              8195308         12    8195296   1% /run/shm
none               102400          0     102400   0% /run/user


$ sudo du / -h --si --max-depth=1 | grep '[0-9]G\>'
2.8G    /usr
4.8G    /var
du: cannot access ‘/proc/4362/task/4362/fd/4’: No such file or directory
du: cannot access ‘/proc/4362/task/4362/fdinfo/4’: No such file or directory
du: cannot access ‘/proc/4362/fd/3’: No such file or directory
du: cannot access ‘/proc/4362/fdinfo/3’: No such file or directory


Can anybody offer me some advice this seems excessive for a basic install really - theres not much running on there

Thanks for any info people

---

### Post by Bashing-om on 2015-10-06
lee42; Hi !

We can get a better sense of what is from the partitioning on the hard drive.
```

sudo fdisk -lu
sudo parted -l
df -h
df -i

```
Between code tags please :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Maybe the root partition ( /dev/sdg1 ) will be relatively small to the other partitions on the drive taking the disk space .

For your reference My system's booting hard drive:
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  2.1G  2.4G  47% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  740K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   21M  2.0G   2% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda2       9.5G  2.5G  6.6G  28% /home
/dev/sda8       4.7G  675M  3.8G  15% /var
sysop@1404mini:~$

```
A very frugal install !

[INDENT][INDENT]partitions, partitions
[INDENT][INDENT][INDENT]what are the partitions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lee42 on 2015-10-07
Thanks

Hope this is ok


```


sudo fdisk -lu


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00083971


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048  3907029167  1953513560   83  Linux


Disk /dev/sdc: 250.1 GB, 250059350016 bytes
81 heads, 63 sectors/track, 95707 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79e8201b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   488397167   244197560   83  Linux


Disk /dev/sdd: 1007 MB, 1007681536 bytes
9 heads, 8 sectors/track, 27335 cylinders, total 1968128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x648f1851


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *         472     1968127      983828    c  W95 FAT32 (LBA)


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f3024e2


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          63  3907024064  1953512001   83  Linux


Disk /dev/sdg: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f09fd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048   216586239   108292096   83  Linux
/dev/sdg2       216588286   250068991    16740353    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdg5       216588288   250068991    16740352   82  Linux swap / Solaris


```

```
 sudo parted -lModel: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  ext4               msftdata




Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2738GB  2738GB  ext4         primary
 2      2738GB  3001GB  262GB   ext4




Model: Inateck  (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ext4




Model: Generic Flash Disk (scsi)
Disk /dev/sdd: 1008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End     Size    Type     File system  Flags
 1      242kB  1008MB  1007MB  primary  fat32        boot, lba




Model: ATA Hitachi HDS5C302 (scsi)
Disk /dev/sde: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4         boot




Model: ATA Hitachi HDS5C302 (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary  ext4         boot




Model: ATA Crucial_CT128MX1 (scsi)
Disk /dev/sdg: 128GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  111GB  111GB   primary   ext4
 2      111GB   128GB  17.1GB  extended
 5      111GB   128GB  17.1GB  logical   linux-swap(v1)



```

```
df -hFilesystem      Size  Used Avail Use% Mounted on
/dev/sdg1       102G   73G   24G  76% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.9G   12K  7.9G   1% /dev
tmpfs           1.6G  1.8M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G   12K  7.9G   1% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdb2       241G   60M  228G   1% /media/IPCam
/dev/sdc1       230G  139G   92G  61% /media/usb0
/dev/sdb1       2.5T  1.3T  1.2T  53% /media/2nd3TBDrive
/dev/sde1       1.8T  612G  1.2T  34% /media/2nd2TBDrive
/dev/sdf1       1.8T  1.7T  167G  91% /media/2TBDrive
/dev/sda1       2.7T  2.1T  626G  78% /media/3TBDrive
/dev/sdd1       958M  579M  379M  61% /media/usb1



```

```
df -i
Filesystem Inodes IUsed IFree IUse% Mounted on
/dev/sdg1 6774784 334485 6440299 5% /
none 2048827 2 2048825 1% /sys/fs/cgroup
udev 2046142 627 2045515 1% /dev
tmpfs 2048827 622 2048205 1% /run
none 2048827 5 2048822 1% /run/lock
none 2048827 4 2048823 1% /run/shm
none 2048827 2 2048825 1% /run/user
/dev/sdb2 16007168 10 16007158 1% /media/IPCam
/dev/sdc1 15269888 946 15268942 1% /media/usb0
/dev/sdb1 167149568 17391 167132177 1% /media/2nd3TBDrive
/dev/sde1 122101760 1513 122100247 1% /media/2nd2TBDrive
/dev/sdf1 122101760 22779 122078981 1% /media/2TBDrive
/dev/sda1 183148544 22958 183125586 1% /media/3TBDrive
/dev/sdd1 0 0 0 - /media/usb1

```

---

### Post by Bashing-om on 2015-10-07
lee42; Hey;

The only problem I see is in sdf1; with 91 % used .. fragmentation of the data is eminent . Suggest that you free up some disk space there.

As to the partition in question - sdg1 - Looks great to me . Room for installation of additional softwares and development tools.
2 partitions on that 128 Gig drive: the operating system and /swap .
It's usable disk space is 102 Gb from a real allotment of 111 GB ( system takes 10% for overhead ?) with 73 gigs presently used, leaving 24 Gigs of free space . So the question I take it is, what is taking up all the disk space of that 73 Gigs ?
Terminal command:
```

du -h --max-depth=1 | sort -hr

``` will give a broad overview of (D)isk (U)sage .
From there one can drill around and go deeper . Maybe it is installed applications, maybe run-a-muck log files taking up  room ?

[INDENT][INDENT]ask the system the right questions
[INDENT][INDENT][INDENT]the system will tell
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

