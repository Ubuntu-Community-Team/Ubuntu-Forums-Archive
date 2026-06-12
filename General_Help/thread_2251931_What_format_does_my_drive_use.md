---
title: "What format does my drive use?"
date: 2014-11-07
forum: General Help
---

### Post by loren41 on 2014-11-07
Received a laptop from a friend.  Removed old Windows XP and installed Ubuntu 14.04 LTS (32-bit).  Not sure what format I selected for the hard drive.  How can I find out?

---

### Post by Bashing-om on 2014-11-07
loren41; Hi !

Default file system format in ubuntu is ext4.
To see the pationing info ( file system format)
```

sudo fdisk -lu

```

[INDENT][INDENT]helps just a bit
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-11-07
If you used the Erase Disk and Install Ubuntu option then you will have the default format of Ext4. If you used the Something Else option then it would have been your choice from a list of file system formats.

Open the Disks utility and it will show the partitions and the format.

Regards.

---

### Post by Bucky Ball on 2014-11-07
*Thread moved to **General Help**.*

... or install Gparted and have a look. No doubt it is EXT4.

---

### Post by loren41 on 2014-11-07
I did as you suggested, but frankly don't know how to read the output.  Is the "Extended' in the sda2 system description line telling me that it is formatted Ext4?

loren41@loren41-Inspiron-1520:~$ sudo fdisk -lu
[sudo] password for loren41: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000cf5b

   Device Boot         Start             End         Blocks    Id   System
/dev/sda1   *           2048    486303743   243150848   83   Linux
/dev/sda2       486305790   488396799       1045505    5    Extended
/dev/sda5       486305792   488396799       1045504   82   Linux swap / Solaris
loren41@loren41-Inspiron-1520:~$

---

### Post by Bucky Ball on 2014-11-07
That's why installing Gparted might be easier if you want a GUI to see what is happening clearly. ;)

Install it via Software Centre. Apparently the disk utility in Ubuntu does something similar but don't use Ubuntu so wouldn't know.

---

### Post by loren41 on 2014-11-07
Thanks for all your help.  Gparted is a good solution.

---

### Post by yancek on 2014-11-07
The command:  df -T will tell you the filesystem type also, that is of all mounted partitions which would have worked in your case.

---

### Post by Bashing-om on 2014-11-08
loren41; Well

> 
but frankly don't know how to read the output. Is the "Extended' in the sda2 system description line telling me that it is formatted Ext4?


I try and explain. In the disk partitioning scheme under consideration, there may only be 4 primary partitions, due to addressing limitations within the partition table. To overcome this 4 partition limit, what is done is make one of these primary partitions an "extended" partition. This extended partition is a container to hold "logical partitions" and has no file system.
```

sudo parted -l

```
note 'swap' as a "logical" partition, in your use case. One may add as many "logical" partitions in the container "extended" as one wishes ( I think the limit for logical partitions is 128 ).
'swap' too has the file system 'linux-swap' rather than ext4.

It is all numbers and space and addressing.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

