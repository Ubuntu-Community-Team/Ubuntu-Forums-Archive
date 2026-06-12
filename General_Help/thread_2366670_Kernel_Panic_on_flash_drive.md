---
title: "Kernel Panic on flash drive"
date: 2017-07-20
forum: General Help
---

### Post by jsmolka on 2017-07-20
> **elolitta said:**
> ...get the error [FONT=Ubuntu]"...[SIZE=2]**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)**[/SIZE]"[/FONT] 

I have no solution, sorry! 
But I have the same problem with my USB stick... 

I tried Ubuntu for a while from the stick and saved my data to the USB stick too. 
Some weeks after I had installed Ubuntu 16.04 on a laptop I wanted to get my data and links from the USB stick. **But it seems that the installation process changed something on the stick!?**

Before the installation booting from the stick worked well and without any problems many times. Now I am not able to boot from the stick anymore -- I get almost the same error message, only the block is (0,0): 

"[SIZE=2][FONT=Ubuntu]... Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/FONT][/SIZE] ..." 

So, what happened to the stick from the installation process? 
And what to do to make the stick bootable again?
(...without loosing my data!!!)

---

### Post by oldfred on 2017-07-20
Moved to your own thread.
While issue may be similar, details are probably different and it is difficult to work with two issues in one thread.

Can you still boot your install?
Post this:
sudo parted -l

---

### Post by jsmolka on 2017-07-20
-----
[B]sudo parted -l
[/B]Model: SanDisk Cruzer Edge (scsi)
Disk /dev/sdb: 31,3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16,4kB  31,3GB  31,3GB  primary  fat32        boot, lba

----- 
**sudo fdisk -l  /dev/sdb**
Disk /dev/sdb: 29,1 GiB, 31260704768 bytes, 61056064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       32 61056063 61056032 29,1G  c W95 FAT32 (LBA)

----- 
**sudo fdisk -l  /dev/sdb***
Disk /dev/sdb: 29,1 GiB, 31260704768 bytes, 61056064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       32 61056063 61056032 29,1G  c W95 FAT32 (LBA)
Disk /dev/sdb1: 29,1 GiB, 31260688384 bytes, 61056032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x20ac7dda

Device      Boot      Start        End    Sectors   Size Id Type
/dev/sdb1p1      3224498923 3657370039  432871117 206,4G  7 HPFS/NTFS/exFAT
/dev/sdb1p2      3272020941 5225480974 1953460034 931,5G 16 Hidden FAT16
/dev/sdb1p3               0          0          0     0B 6f unknown
/dev/sdb1p4        50200576  974536369  924335794 440,8G  0 Empty

Partition table entries are not in disk order.

---

### Post by oldfred on 2017-07-20
I do not know how persistent installs now work. 
I normally just have a second data partition.

Can you manually mount sdb1 and see data in it?

---

### Post by jsmolka on 2017-07-20
file:///media/jes/DB13-695A/boot
file:///media/jes/DB13-695A/casper
file:///media/jes/DB13-695A/dists
file:///media/jes/DB13-695A/install
file:///media/jes/DB13-695A/LinuxLive USB Creator
file:///media/jes/DB13-695A/pics
file:///media/jes/DB13-695A/pool
file:///media/jes/DB13-695A/preseed
file:///media/jes/DB13-695A/syslinux
file:///media/jes/DB13-695A/VirtualBox
file:///media/jes/DB13-695A/casper-rw
file:///media/jes/DB13-695A/ldlinux.c32
file:///media/jes/DB13-695A/ldlinux.lan
file:///media/jes/DB13-695A/ldlinux.sys
file:///media/jes/DB13-695A/md5sum.txt
file:///media/jes/DB13-695A/README.diskdefines
file:///media/jes/DB13-695A/Remove_LiLi.bat
file:///media/jes/DB13-695A/SmartClean.ini

---------
But not my data files... 
They are hidden (I assume you know that).

---

### Post by oldfred on 2017-07-20
What is in casper-rw, I think that is where persistence data is.

---

### Post by jaxom98 on 2017-07-20
Is the length of time to "kernal panic getting shorter each time you try to boot? If so stop.The time will get shorter until you have total lockup. I had to do a full reinstall of the OS. Decide on weather to get a professional to retrieve your data, if you are not fully backed up.
If you are getting to the same point/ error message each time then you have a different problem.
Good luck.

---

### Post by jsmolka on 2017-07-21
@jaxom98
Thanks
But I "*have a different problem*."

@oldfred
How could I look into casper-rw (the 4 GB of persistent data)?

Even if I could find some data in there it would not be all of it (e.g. browser links). 
The best way would be to make the flash bootable again. 

I hadn't expected that the installation changes things **on the flash drive too[SIZE=3]!?[/SIZE]** 
The questions are: What was changed? -and- How to undo that?


-- EDIT -----------------------
While other files on the pen drive are still tagged with the 02/15/2017, 
e.g. the [SIZE=2]**initrd.lz **[/SIZE]was changed to 06/20/2017 (the installation date)!?

---

### Post by oldfred on 2017-07-21
What installation tool did you use to create flash drive?

And my understanding of Flash drive is supposed to be like a DVD, nothing is changed on flash drive. And if you add persistence to allow saving something, only the persistence file has the changes. If a driver for example downloaded, it has to be reinstalled every reboot, but not downloaded as in persistent file.

But I have never used persistent install and rarely flash drive as installer. I use flash drives for full installs or grub only boot of many ISO as a repair flash drive. And have larger data partitions on flash drives for backup use.
And assumption with flash drives is life is not long, but should be usable for a while.

And any other assumption is that any valuable data where ever stored is backed up.

If you can open flash drive, have you tried to drill down in the casper-rw folder?

You could try photorec, if you cannot get flash drive to boot.

---

### Post by jsmolka on 2017-07-21
Let me repeat it to make it clear: 

1. In February I made the stick running the Ubuntu Live/Persistent system. 

2. From February to June I tested Ubuntu with that USB stick without any problem. 

3. In June I installed Ubuntu onto a laptop from that flash drive. (again easy without any problem) 

4. After the installation it was not possible to start the Ubuntu Live/Persistent system from the stick anymore!? 

----------------------------------- 
An installation from a DVD can not change the DVD... 
The installation from a flash drive should not change the flash drive content either. 

But it did. A bootable flash drive was no more bootable after the installation!?   ](*,)

HOW TO UNDO this unexpected change? 
========================

---

### Post by oldfred on 2017-07-21
Not sure if some other issue, or if flash drive was seen as sda, then installer may have then changed files on sda.
Does install on hard drive work ok?
Are you booting flash drive in same mode UEFI or BIOS?

Did you try to drill down using Nautilus on casper-rw folder?

What brand/model system and what video card/chip?

If you can download ISO of same version as your original flash drive, you may be able to copy initrd.lz onto flash drive.

---

### Post by jsmolka on 2017-07-22
> **oldfred said:**
> If you can download ISO of same version as your original flash drive, you may be able to copy initrd.lz onto flash drive.

@oldfred
THANK YOU so much !!! 

While the original initrd.lz had about 27 MiB -- the file on the USB stick had only 23 B !? 

**I copied the original initrd.lz to the stick** and it booted like before. 

[SIZE=3]:):-D[/SIZE]

---

