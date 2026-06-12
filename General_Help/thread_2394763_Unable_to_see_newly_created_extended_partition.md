---
title: "Unable to see newly created extended partition"
date: 2018-06-20
forum: General Help
---

### Post by rahul45 on 2018-06-20
Hi There,

I am unable to use my newly created extended partition under /dev/sda3
It doesn't show when i do fdisk -l, however when i run fdisk -l /dev/sda3 it shows the partition information 
I need to mount this partition for some testing purpose 
Any idea would be appreciated 


Outputs :- 


```
fdisk -l

Disk /dev/sda: 60 GiB, 64424509440 bytes, 125829120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5c9dabc9

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sda1           2048 69208063 69206016   33G 83 Linux
/dev/sda2       69210110 73398271  4188162    2G  5 Extended
/dev/sda3       73398272 95105023 21706752 10.4G 83 Linux
```


root@ubuntu:~# 


```
root@ubuntu:~# fdisk /dev/sda3

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): e
Partition number (1-4, default 1): 1
First sector (2048-21706751, default 2048): 5120
Last sector, +sectors or +size{K,M,G,T,P} (5120-21706751, default 21706751): 

Created a new partition 1 of type 'Extended' and of size 10.4 GiB.

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Re-reading the partition table failed.: Invalid argument

The kernel still uses the old table. The new table will be used at the next reboot or after you run partprobe(8) or kpartx(8).
```

```
root@ubuntu:~# partprobe
root@ubuntu:~# 
```

```
fdisk -l 


Disk /dev/sda: 60 GiB, 64424509440 bytes, 125829120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5c9dabc9

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sda1           2048 69208063 69206016   33G 83 Linux
/dev/sda2       69210110 73398271  4188162    2G  5 Extended
/dev/sda3       73398272 95105023 21706752 10.4G 83 Linux
```


```
root@ubuntu:~# 
root@ubuntu:~# blkid
/dev/sda1: UUID="1406a0e8-8740-433a-bc33-9fe88242d678" TYPE="ext4" PARTUUID="5c9dabc9-01"
/dev/sda3: UUID="2d2a5c9b-f472-44a2-89ed-264189e4cc07" TYPE="ext4" PTUUID="64e7d865" PTTYPE="dos" PARTUUID="5c9dabc9-03"
root@ubuntu:~# 
root@ubuntu:~#
```

---

### Post by Bashing-om on 2018-06-20
rahul45; Hello - Welcome to the forum.

Do you understand that an "extended"  partition is a container to hold additional "logical" partitions ?
Within the extended partition one makes up these logical partitions .. here in your case is a small extended partition of 2 Gigs.
You have 2 primary partitions - sda1 and sda3 containing linux file systems . 

What is your goal that you are attempting to achieve ? We can then offer better guidance .

one of my drives:
```

Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc6c4079f

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1  *         2048  16386047  16384000  7.8G 83 Linux
/dev/sdb2        16386048  36866047  20480000  9.8G 83 Linux
/dev/sdb3        36866048  49154047  12288000  5.9G 83 Linux
/dev/sdb4        49154048 172034047 122880000 58.6G  5 Extended
/dev/sdb5        49156096 110596095  61440000 29.3G 83 Linux
/dev/sdb6       110598144 131078143  20480000  9.8G 83 Linux
/dev/sdb7       131080192 151560191  20480000  9.8G 83 Linux
sysop@x1810:~$

```
where sdb5, sdb6 and sdb7 are "logical" partitions within that "extended" sdb4 partition.

[INDENT]help is what we do
[/INDENT]

---

