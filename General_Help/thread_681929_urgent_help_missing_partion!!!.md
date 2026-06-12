---
title: "urgent help missing partion!!!"
date: 2008-01-29
forum: General Help
---

### Post by RazeRules on 2008-01-29
here's the situation,
i have 2 hard disks 80gb each
one of them has windows xp pro installed on an NTFS partition and another 4 fat32 partitions
and i've just installed ubuntu 7.10 on the 2nd hard disk at the first 10 db of the disk to make a dual-boot system and there's another 4 fat32 partitions on this hd.
the problem is after ubuntu installed i found there's a partition missing on the ubuntu's hard disk which is sdb7 (i found only sdb5, sdb6, sdb8 )
anyone got any idea about what might be the problem?? and can i recover the data on that partition anyhow??
thx in advance.

---

### Post by bodhi.zazen on 2008-01-29
Lets look, please post the output of :

```
sudo fdisk -l
```

---

### Post by RazeRules on 2008-01-29
> **bodhi.zazen said:**
> Lets look, please post the output of :

```
sudo fdisk -l
```

thnx for ur reply, and here's the output:


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf235f235

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9729    67906755    f  W95 Ext'd (LBA)
/dev/sda5            1276        2550    10241406    b  W95 FAT32
/dev/sda6            2551        5100    20482843+   b  W95 FAT32
/dev/sda7            5101        7650    20482843+   b  W95 FAT32
/dev/sda8            7651        9729    16699536    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b272b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         973     7815591   83  Linux
/dev/sdb2             974        9729    70332570    f  W95 Ext'd (LBA)
/dev/sdb5            1276        2551    10243768+   b  W95 FAT32
/dev/sdb6            2551        5101    20480008+   b  W95 FAT32
/dev/sdb7            5102        7649    20466778+   b  W95 FAT32
/dev/sdb8            7650        9729    16700008+   b  W95 FAT32
/dev/sdb9             974        1275     2425752   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by bodhi.zazen on 2008-01-29
Your partitions are out of order, but I think they are all there.

We will need to mount the partitions and look at the contents ...

---

### Post by RazeRules on 2008-01-29
> **bodhi.zazen said:**
> Your partitions are out of order, but I think they are all there.

We will need to mount the partitions and look at the contents ...

sorry but i dont know how to do that, 
this is my first day on ubuntu and my 2nd time on a linux. :( can u explain further plz?

---

### Post by bodhi.zazen on 2008-01-29
Well, first lets see how many of these partitions were auto mounted, look in nautilus, places -> home

navigate to /media

Otherwise :

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by RazeRules on 2008-01-29
ok, here's my /etc/fstab after editing ntfs & fat entries, but as u can see sdb7 still absent: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a9344187-f81d-461a-9e04-a2d134db60a8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8278156778155AED /media/windows     ntfs    defaults,umask=0222,gid=46 0       0
# /dev/sda5
UUID=0F25-16EE  /media/sda5     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda6
UUID=0B41-16F5  /media/sda6     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda7
UUID=1439-16FC  /media/sda7     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda8
UUID=3545-1701  /media/sda8     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sdb5
UUID=1C26-0814  /media/sdb5     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sdb6
UUID=C3C5-F367  /media/sdb6     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sdb8
UUID=464A-8E21  /media/sdb8     vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sdb9
UUID=7e3d76ed-8f82-4535-9ae6-351fe915ff0e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by RazeRules on 2008-01-30
I used Linux Rescue Disk 0.4.3 and i ran "testdisk" from there, i found the missing partition there and i was even able to access my files but i still cant see this fat32 partition niether on ubuntu nor on windows xp, what should i do now?? :confused: worth telling that when i ran testdisk it printed that the heads/cylenders is 255 and it should be corrected to 240, also when i ran deeper search it found a read error somewhere at the missing partition. any ideas about what should i do next ??

---

### Post by RazeRules on 2008-01-30
is it safe to change the disk geometry using "testdisk" ? may that solve the problem ?

---

### Post by RazeRules on 2008-01-30
sorry for pumping ,.. but i need some help here :(

---

### Post by bodhi.zazen on 2008-01-30
I have changed the partition order with fdisk

You need to know the geometry. 

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

[http://www.freeos.com/articles/3935/](http://www.freeos.com/articles/3935/)


launch fdisk

Delete the partitions

Make new partitions, in on order of cylinder # , one at at time.

Write to disk

reboot.

BUT, this is not necessary, and if you do not understand how to do it you can have problems, in which case you can delete the partition table and try restoring it with test disk.

I advise you look at the link I gave you for fstab.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by RazeRules on 2008-01-30
..................???

---

### Post by RazeRules on 2008-01-30
isnt deleting the partiton means losing my data ?

---

### Post by bodhi.zazen on 2008-01-30
Well, why not add an entry for your partition in fstab ?

/dev/sdb7 /media/sdb7 vfat auto,users,uid=1000,gid=100,umask=007 0 0

Or by UUID if you prefer, list UUID with 

```
blkid | grep sdb7
```

UUID=xxx.xxx.xxx /media/sdb7 vfat auto,users,uid=1000,gid=100,umask=007 0 0

If you have questions, you will need to be more specific then > ..................???

You will not lose data (deleting a partition) unless you format the partition or make a mistake.

---

### Post by RazeRules on 2008-01-30
thnx alot for ur care, i'll try to edit fstab first, but i doubt it will work since this partition is appeared to be unformated area on gparted even though i can access its files through testdisk. then i'll try to delete and re-create the partitions as u mentioned, i'll get back to u with the results. thnx again

---

### Post by RazeRules on 2008-01-31
i tried the fstab thing but it doesnt work. so i deleted all the partitions using testdisk.
here's the new output for sudo fdisk -l :
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf235f235

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9729    67906755    f  W95 Ext'd (LBA)
/dev/sda5            1276        2550    10241406    b  W95 FAT32
/dev/sda6            2551        5100    20482843+   b  W95 FAT32
/dev/sda7            5101        7650    20482843+   b  W95 FAT32
/dev/sda8            7651        9729    16699536    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b272b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         973     7815591   83  Linux
/dev/sdb2             974        1275     2425783+   f  W95 Ext'd (LBA)
/dev/sdb5             974        1275     2425752   82  Linux swap / Solaris

```

now what exactly should i do to restore my 4 partions on this drive?

---

### Post by RazeRules on 2008-01-31
is this a good thing or a bad one ?

---

### Post by RazeRules on 2008-01-31
i've just tried now to creat new partitions usin fdisk with same privieous cylinder # but they came up to be linus filesystem not fat32 so i quit without saving, is that means i lost my data ?

---

### Post by bodhi.zazen on 2008-01-31
Unmount the partition

Make an extended partition cylinders  974    ->    9729 

Then make you other partition, in cylinder order 

1.  974        1275     2425752   82  Linux swap / Solaris

2. 1276        2551    10243768+   b  W95 FAT32

3. 2551        5101    20480008+   b  W95 FAT32

4. 5102        7649    20466778+   b  W95 FAT32

5. 7650        9729    16700008+   b  W95 FAT32

When you make a partition, use the correct hex code (82 for swap, 

[quote]Command (m for help): t
Partition number (1-4): 2
**Hex code (type L to list codes): 82**
Changed system type of partition 2 to 82 (Linux swap)      
Command (m for help): p[/code]

To list the hex codes, use the help (type l)

[quote]Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
**   l   list known partition types**
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): [/code]

Use the code for FAT32

Save and exit

Reboot

---

### Post by RazeRules on 2008-01-31
sorry for pumping

---

### Post by RazeRules on 2008-01-31
i did exactly what u told me, everything was fine and i had the same partitioning status as before, but the partitions did not appear on ubuntu and appeared unformatted on windows xp. all i'm caring about now is my data, is there any way to recover the data then re-partition the whole disk after that ?

---

### Post by bodhi.zazen on 2008-01-31
Did you reboot (I assume so, just checking though) ?

If so, can you post the output of :

```
sudo fdisk -l
```

---

