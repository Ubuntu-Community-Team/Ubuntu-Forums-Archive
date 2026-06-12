---
title: "usb drive not recognized"
date: 2014-10-31
forum: General Help
---

### Post by kirtan_parmar on 2014-10-31
hello,
I am a new  linux user. I plug in my usb drive yet the drive doesn't seem to get recognized. It works perfectly on my windows laptop. I searched online for some help but I am confused. I ran a few commands in the terminal, hope that helps.
```
lsusb
```
```
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 005: ID 0011:7788  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse receiver
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


```
lsblk
```
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0 295.1G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0     3G  0 part [SWAP]
sdb      8:16   1   7.8G  0 disk 
sr0     11:0    1  1024M  0 rom  

```


```
sudo fdisk -l
```
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1d3b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   618872831   309435392   83  Linux
/dev/sda2       618874878   625141759     3133441    5  Extended
/dev/sda5       618874880   625141759     3133440   82  Linux swap / Solaris


Disk /dev/sdb: 8388 MB, 8388608000 bytes
64 heads, 32 sectors/track, 8000 cylinders, total 16384000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x500a0dff


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  1948285285  3650263507   850989111+  6e  Unknown
/dev/sdb2   ?           0           0           0   74  Unknown
/dev/sdb4        28049408    28049848         220+   0  Empty


Partition table entries are not in disk order



```

any help is appreciated.

---

### Post by stalkingwolf on 2014-10-31
does it show up in gparted or under computer?

---

### Post by kirtan_parmar on 2014-10-31
it does as /dev/sdb in gparted.

---

### Post by ajgreeny on 2014-10-31
```
Disk /dev/sdb: 8388 MB, 8388608000 bytes
64 heads, 32 sectors/track, 8000 cylinders, total 16384000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x500a0dff


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  1948285285  3650263507   850989111+  6e  Unknown
/dev/sdb2   ?           0           0           0   74  Unknown
/dev/sdb4        28049408    28049848         220+   0  Empty


Partition table entries are not in disk order
```
As you can see from the fdisk output there is something wrong with the partition table on that disk.

If there is anything of value on it I suggest you copy it all of to your windows laptop then using gparted in Ubuntu make a new partition table from the Device menu, and then reformat it to fat32 or ntfs, whichever you prefer.

If you used Windows to format the disk in the first place that may be the reason for Ubuntu not being able to see it; Windows can do some strange things when making partitions and it is usually much more advisable to partition for Linux with a Linux application.

---

