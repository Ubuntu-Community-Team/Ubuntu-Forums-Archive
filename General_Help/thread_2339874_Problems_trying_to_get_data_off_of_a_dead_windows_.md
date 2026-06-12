---
title: "Problems trying to get data off of a dead windows 10 laptop"
date: 2016-10-13
forum: General Help
---

### Post by McBeef on 2016-10-13
I had a Centos install about a decade ago that I played around with  briefly but for all intents I am know very little about linux. Anyways, my windows 10 laptop recently died, displaying the message "Operating System not found" on bootup. The laptop has two hard drives, on with the OS and one that has the data on it that I need. I googled around a bit a read about a method for retrieving data from dead laptops using linux setup on a USB flash drive. I followed [these instructions]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") with the exception that I used Rufus instead of ImgBurn. I booted into linux successfully on the dead laptop. The drives were not listed in the UI, but I found some bash commands online that revealed them:

> ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk
&#9500;&#9472;sda1   8:1    0   931G  0 part
&#9492;&#9472;sda2   8:2    0   488M  0 part
sdb      8:16   0 931.5G  0 disk
&#9492;&#9472;sdb1   8:17   0   500M  0 part
sdc      8:32   1   3.8G  0 disk
&#9492;&#9472;sdc1   8:33   1   3.8G  0 part /cdrom
sr0     11:0    1  1024M  0 rom 
sr1     11:1    1    24M  0 rom 
loop0    7:0    0   1.4G  1 loop /rofs

Based on the size, I'm guessing that sda1 is the windows install and the non partitioned portion of sdb is my data. Based on the instructions, proceeding further:

> ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# mkdir /media/disk
root@ubuntu:~# lsblk -f
NAME   FSTYPE   LABEL           UUID                                 MOUNTPOINT
sda                                                                 
&#9500;&#9472;sda1                                                              
&#9492;&#9472;sda2 ntfs                     4642EB8E42EB80D3                    
sdb                                                                 
&#9492;&#9472;sdb1 ntfs     System Reserved CAF89712F896FBBF                    
sdc                                                                 
&#9492;&#9472;sdc1 vfat     UBUNTU 16_0     3835-2A16                            /cdrom
sr0                                                                 
sr1                                                                 
loop0  squashfs                                                      /rofs
root@ubuntu:~# df -h -T
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  9.5M  1.6G   1% /run
/dev/sdc1      vfat      3.8G  2.4G  1.4G  63% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
/cow           overlay   7.9G   61M  7.8G   1% /
tmpfs          tmpfs     7.9G  288K  7.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     7.9G  132K  7.9G   1% /tmp
tmpfs          tmpfs     1.6G   92K  1.6G   1% /run/user/999

First a try at windows:

> root@ubuntu:~# mount -t ntfs-3g /dev/sda1 /media/disk -o force
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sdb1 works OK:

> 
root@ubuntu:~# mount -t ntfs-3g /dev/sdb1 /media/disk -o force
root@ubuntu:~# umount /dev/sdb1

But the data drive will not:

> root@ubuntu:~# mount -t ntfs-3g /dev/sdb /media/disk -o force
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

So what I'm wondering is how do I go about getting my data off of the hard drive?

---

### Post by SeijiSensei on 2016-10-13
/dev/sdb refers to the entire drive.  Since it has no filesystem it cannot be mounted.

What did you see when you mounted /dev/sdb1 with
```
# mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

---

### Post by oldfred on 2016-10-13
Until I just went back to read man page I did not know force is obsolete.
see:
man ntfs-3g

>       ro     Mount filesystem read-only. Useful if Windows is  hibernated  or
              the NTFS journal file is unclean.

     force  This  option  is obsolete. It has been superseded by the recover
              and norecover options.




---

### Post by McBeef on 2016-10-13
Thank you for responding.

> **SeijiSensei said:**
> /dev/sdb refers to the entire drive.  Since it has no filesystem it cannot be mounted.

Is the categorically true because only partitions have filesystems and not drives or is it just because this drive in particular is having problems?

> **SeijiSensei said:**
> What did you see when you mounted /dev/sdb1 with
```
# mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

Here is sda2:
[IMG]http://i.imgur.com/f3lgbQK.png[/IMG]

And here is sdb1:
[IMG]http://i.imgur.com/JWbzVnw.png[/IMG]

Not the data I'm looking for. They both appear to be OS stuff.

Let's assume that whatever killed my computer also took out the main partition of sdb and also rendered sda1 somehow unworkable, both formerly NTFS formatted. Let's also assume that the data I'm looking for is or at least was either in sda1 or in the unorganized void of sdb. Is there a way to retrieve this data?

---

### Post by oldfred on 2016-10-13
If hibernated Linux will not auto mount.
But partition table should show which is which.
Post these:
sudo parted -l
sudo fdisk -lu

---

### Post by McBeef on 2016-10-14
Thank you for responding oldfred.

> **oldfred said:**
> If hibernated Linux will not auto mount.
But partition table should show which is which.
Post these:
sudo parted -l
sudo fdisk -lu

Here is parted:
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               boot
 2      1000GB  1000GB  512MB   primary  ntfs         diag


Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  525MB  524MB  primary  ntfs         boot


Model: SanDisk U3 Titanium (scsi)
Disk /dev/sdc: 4022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4022MB  4021MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label
Model: Unknown (unknown)                                                 
Disk /dev/sr1: 25.2MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 


```

And here is fdisk:

```
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1459982336 bytes, 2851528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x119dbe44

Device     Boot      Start        End    Sectors  Size Id Type
/dev/sda1  *          2048 1952518935 1952516888  931G  7 HPFS/NTFS/exFAT
/dev/sda2       1952520192 1953519615     999424  488M 27 Hidden NTFS WinRE


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x119dbe4d

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 1026047 1024000  500M  7 HPFS/NTFS/exFAT




Disk /dev/sdc: 3.8 GiB, 4022337536 bytes, 7856128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2802839e

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *     2048 7856127 7854080  3.8G  c W95 FAT32 (LBA)
ubuntu@ubuntu:~$

```

---

### Post by oldfred on 2016-10-14
You only show one tiny NTFS boot partition on sdb. Or nothing to mount.
Did you delete partitions?

See what testdisk shows?
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

