---
title: "Partitioning"
date: 2007-08-20
forum: General Help
---

### Post by Dylnuge on 2007-08-20
Hello,

How do I partition in Ubuntu? In Windows, I know that by running a defragmenter and moving files to the front of the disk, I can easily resize partitions. Linux has a journaled file system, which means no defragmenters, does this mean I won't lose data through repartitioning? I only want to make a partition bigger-but since it is behind the boot partition and swap partition, I would need to completely move those back into the unallocated space to make room.

Thanks,
Dylan

PS: I am working on a laptop with a small hard drive (ok, not that small, but as my Desktop Replacement, I need a place for videos, photos, websites, client files, programs, source code, etc.). I was considering buying a second hard drive (external). What would I map it to? I could use /home/dnugent/drive2 (or something similar), but that would leave out anyone else (there are a few other users who borrow my laptop), or just /home/drive2, which would require some grouping. Plus, a lot of my files are programs-could I map certain programs there, or would that mess up the system should the drive be absent?

---

### Post by jnorthr on 2007-08-20
Yes, you would want to defrag anyway and do a full backup too before starting on a re-partition. The ubuntu 7.0.4. live cd has a supergrub utility built in to help with this task. I've done this one on my old laptop. Just shove all the windows data up front then chop off the back of the windows partition for ubuntu. I put in a swap partition next about 2 or 3 times ram size, then i did a /home partition of a few gigs then cos i like to develop and don't want to reinstall java and eclipse, i made a /usr/local partition of a few gigs for them then left the final partition for / - the root. ubuntu can read/write the windows partition if it's fat32 format. So i can STILL access all my java source code from within ubuntu IDE without switching back to windows. (sorry maybe i missed your point on this one )

The external drive will probably be assigned it's own mount point in the /media folder. If it' like mine, i have an external usb freecom drive about 20Gb and it has it's own mount point, once ithas that you can use it like any other file in the file system.

---

### Post by bodhi.zazen on 2007-08-20
> **Dylnuge said:**
> Hello,

How do I partition in Ubuntu? In Windows, I know that by running a defragmenter and moving files to the front of the disk, I can easily resize partitions. Linux has a journaled file system, which means no defragmenters, does this mean I won't lose data through repartitioning? I only want to make a partition bigger-but since it is behind the boot partition and swap partition, I would need to completely move those back into the unallocated space to make room.

No, you can do this with gparted, although you need a newer version, such as the gparted live CD :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)


> Thanks,
Dylan

PS: I am working on a laptop with a small hard drive (ok, not that small, but as my Desktop Replacement, I need a place for videos, photos, websites, client files, programs, source code, etc.). I was considering buying a second hard drive (external). What would I map it to? I could use /home/dnugent/drive2 (or something similar), but that would leave out anyone else (there are a few other users who borrow my laptop), or just /home/drive2, which would require some grouping. Plus, a lot of my files are programs-could I map certain programs there, or would that mess up the system should the drive be absent?

You can place (mount) the new drive wherever you would like and call it what you will.

The "standard" location is in /media

Permissions are handled by, well permissions.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by Dylnuge on 2007-08-20
I am not asking about Windows-I don't have a Windows partition. I have partitions including /boot, followed by swap, followed by /, followed by /home. My point is that I removed an old partition which was before /boot. I want to use the new unallocated space to:

1. Move /boot and swap back to the front of the drive. They are fine sizes.
2. Strech / out and move it back a bit to make more room for /home.
3. Strech /home out.

Will using gparted or something else be possible. I need to know how to keep my Ubuntu data while moving my parts around.

Thanks,
Dylan

---

### Post by bodhi.zazen on 2007-08-20
gparted will do this for you. see the links I gave you for documentation. 

You will not loose your ubuntu data unless you format the partition.

You can back up your data (not a bad idea) before you start if you like.

I think you will need to re-install grub after all that moving.

---

### Post by merlinus on 2007-08-20
And if your /etc/fstab uses UUIDs for partitions, you will need to correct that as well.  They will change with resizing and moving.

```

sudo fdisk -l
blkid

```

Compare with those in /etc/fstab and correct if needed.

-merlin

---

### Post by Dylnuge on 2007-08-26
Sorry, a but new to this, and I don't know exactly what to do with my UUIDs.

fdisk -l:
```
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    6  FAT16
/dev/sda2   *           6        8954    71882842+   7  HPFS/NTFS
/dev/sda3           11521       11977     3670852+  db  CP/M / CTOS / ...
/dev/sda4            8955       11520    20611395    f  W95 Ext'd (LBA)
/dev/sda5            8955        9077      987966   83  Linux
/dev/sda6            9078        9332     2048256   82  Linux swap / Solaris
/dev/sda7            9333       10426     8787523+  83  Linux
/dev/sda8           10427       11520     8787523+  83  Linux

Partition table entries are not in disk order
```

blkid:
```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0808" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="50a4bf9a-5366-43e5-bf73-5d6b3ca20a0d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="c72889cc-5ced-4f6e-8a90-38f2e0e50b7f" TYPE="swap" 
/dev/sda7: UUID="cd8521e7-03a6-4490-b6fd-e280e758df72" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="114cde8c-935e-4d4a-8591-14108bbf36cb" SEC_TYPE="ext2" TYPE="ext3" 
```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=cd8521e7-03a6-4490-b6fd-e280e758df72 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=50a4bf9a-5366-43e5-bf73-5d6b3ca20a0d /boot           ext3    defaults        0       2
# /dev/sda8
UUID=114cde8c-935e-4d4a-8591-14108bbf36cb /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D6-0808  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=1C245B25245B00E6 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=c72889cc-5ced-4f6e-8a90-38f2e0e50b7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

PS: How do I burn an iso in Linux?

---

### Post by ronacc on 2007-08-26
easiest way to burn an iso in gnome ( I assume you are running Ubuntu) is to insert a blank cd or dvd and when the box pops up asking what you want to do click ignore . then in nautilus browse to the ISO and right click it  and select  write to disk.

---

