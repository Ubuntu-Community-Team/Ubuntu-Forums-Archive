---
title: "trouble mounting all of primary disk drive in 7.10"
date: 2008-02-28
forum: General Help
---

### Post by jsstuart on 2008-02-28
I just installed Ubuntu 7.10, and most of my primary disk drive is not being recognized.

Here is the info from parted

Disk /dev/sda: 20.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  15.1GB  15.1GB  primary   ext3              
 3      15.1GB  18.9GB  3808MB  primary   ext3         boot 
 2      18.9GB  20.0GB  1086MB  extended                    
 6      18.9GB  19.2GB  238MB   logical   linux-swap        
 5      19.2GB  20.0GB  847MB   logical   linux-swap  

And from df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              3660632   3272752    201928  95% /
varrun                  249792       104    249688   1% /var/run
varlock                 249792         0    249792   0% /var/lock
udev                    249792        68    249724   1% /dev
devshm                  249792         0    249792   0% /dev/shm
lrm                     249792     34696    215096  14% /lib/modules/2.6.22-14-generic/volatile

As you can see, the bulk of the disk drive is not getting mounted.  I tried:
% mount /dev/sda1 /usr/home

That does mount a new partition with ~15 GB of space, but the resulting file system includes a copy of everything in /.  

My /etc/fstab looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fe39df3f-145b-4792-b444-7d3b315a624a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=9dbb8a9f-ab5a-4a46-88b2-46a0442a9455 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

So it seems that I need to tell it to use /dev/sda1 instead of /dev/sda3, but I'm not sure how to do that with the symbolic names being used.  Any pointers on how to fix this?

Thanks,
   Scott

---

### Post by Yellow Pasque on 2008-02-28
I'm kind of confused. Can you run some commands for us?
```
sudo fdisk -l
sudo blkid
```

---

### Post by jsstuart on 2008-02-29
OK, here is the output from fdisk and blkid.  

[FONT="Lucida Console"]
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05490548

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1837    14755671   83  Linux
/dev/sda2            2301        2432     1060290    5  Extended
/dev/sda3   *        1838        2300     3719047+  83  Linux
/dev/sda5            2330        2432      827316   82  Linux swap / Solaris
/dev/sda6            2301        2329      232879+  82  Linux swap / Solaris

Partition table entries are not in disk order
meg@scott-laptop:~$ sudo blkid
/dev/sda1: LABEL="/" UUID="7161cef4-e0a5-44fe-bebd-03ad31216ebe" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: UUID="fe39df3f-145b-4792-b444-7d3b315a624a" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="c9286662-72b7-412c-a61a-91cdb27f187d"
/dev/sda6: TYPE="swap" UUID="9dbb8a9f-ab5a-4a46-88b2-46a0442a9455"


[/FONT]

---

### Post by jsstuart on 2008-03-02
For the record, I figured out what was wrong with the disk partitioning.  When I installed 7.10, instead of putting it on top of 6.04 in the primary partition, the install CD created a very small partition at the end of the primary partition from 6.04, and installed 7.10 there.  I figured there was really no way to fix it without reinstalling, so I reinstalled and made sure that the new install created one large partition (plus the necessary swap).

Now 7.10 is running nicely.

---

