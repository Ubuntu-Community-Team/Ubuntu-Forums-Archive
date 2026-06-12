---
title: "How to mount my old /home partition?"
date: 2008-04-27
forum: General Help
---

### Post by Bungo Pony on 2008-04-27
So, I did a fresh install from Gutsy to Hardy. Everything looks like crap, but we'll get to that in a minute...

After I installed Gutsy, I put my /home folder on a seperate partition. But now I have no clue how to mount it. 

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac2d1e7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3442    27647833+   7  HPFS/NTFS
/dev/sda3            3443       16203   102502732+  83  Linux
/dev/sda4           16204       19896    29664022+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d194

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3838    30828703+  83  Linux
/dev/sdb2           14430       14593     1317330    5  Extended
/dev/sdb3            3839       14429    85072207+  83  Linux
/dev/sdb5           14430       14593     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order
bpony@linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=221ec78c-9a39-4d13-a806-81804808f9bf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=5b1c979a-ac3a-4cde-b7e9-fed0d3b00cbf none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

My /home partition is on sdb3. How do I mount it?

Second, the nvidia_new driver is enabled, but not in use. My screen is sitting at 800x600. What the heck is going on? I've never had this problem!

---

### Post by p_quarles on 2008-04-27
Well, the easiest way to mount a partition as /home is to select it when you do partitioning. This can be done easily by selecting the "manual" partitioning option during installation. 

You can still do this, of course, using the Ubuntu live CD or the Gparted live CD. 

You can also manually add a line to /etc/fstab, something like:
```
UUID={the partition's uuid} /home ext3 defaults 0 2
```
I don't know if it will cause any problems, but I would remove any home directories created on the root partition to avoid the possibility of confusing the filesystem.

---

### Post by mali2297 on 2008-04-27
To find out the UUID, type
```

blkid /dev/sdb3

```
in the terminal.


> **p_quarles said:**
> W
You can also manually add a line to /etc/fstab, something like:
```
UUID={the partition's uuid} /home ext3 **defautls** 0 2
```

I guess you mean something like **defaults**. Another suggestion is to use the options **nodev,nosuid** (from [here]("http://psychocats.net/ubuntu/separatehome")).

---

### Post by russo.mic on 2008-04-27
OR,  you could just type

sudo mount /dev/sdb3 /somelocation/somewhere

---

### Post by p_quarles on 2008-04-27
> **mali2297 said:**
> I guess you mean something like **defaults**.
D'oh! 

Thanks, and fixed.

---

