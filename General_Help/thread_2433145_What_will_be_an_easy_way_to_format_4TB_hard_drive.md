---
title: "What will be an easy way to format 4TB hard drive"
date: 2019-12-14
forum: General Help
---

### Post by satimis on 2019-12-14
Hi all.

What will be an easy way to format a 4TB WD hard drive. Ubuntu 18.04 has been installed on it.  I'll use it for storage only without partition.

$ sudo fdisk -l```

Units: sectors of 1 * 512 = 512 bytes
Disk /dev/loop1: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk /dev/loop4: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop6: 88.5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop7: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F3A8D40E-D988-4EF7-8FB7-B1F978474D92

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048   1050623   1048576   512M EFI System
/dev/sdb2  1050624 976771071 975720448 465.3G Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 464.3 GiB, 498539167744 bytes, 973709312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

The device is on /dev/sda

I learned a bitter lesson before running Activities-->Disks to format it.  It took more than 10 hrs to complete.

```

$ sudo mkfs.ext3 /dev/sda

```

also takes sometime to finish

Thanks in advice.

Regards
satimis

---

### Post by vanadium on 2019-12-14
By far the fastest way is to use mkfs, like you did. Why did you use ext3? ext4 is the current up to date format.

Also create a partition first.

AN alternative to using the command line for partitioning and formatting is to use the utility "Disks", which is by default installed on Ubuntu.

---

### Post by Dennis N on 2019-12-14
> What will be an easy way to format a 4TB WD hard drive? Ubuntu 18.04 has been installed on it. I'll use it for storage only without partition.
I assume you intend to erase the existing Ubuntu? And Windows is not to be used?
```
sudo mkfs.ext3 /dev/sda
```
Without any partition? - this &#8593;  is not the correct way. You should always use partitions with Linux. To reuse a disk for Linux use, 1) create a new partition table on the disk - use GPT for type of partition table 2) create at least one partition and format the partition(s) ext4, not ext3. I suggest you use gparted from your existing install for these tasks, and avoid the terminal.

---

### Post by TheFu on 2019-12-14
Always, always, partition a disk. ALWAYS!

Backup any data you want to keep.

Setup a GPT partition table. With 4TB, GPT is mandatory.

Setup any partitions. The size of those partitions should depend on how you will backup, restore, and use the partitions.
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) is my setup with reasons WHY.

If you use LVM and ext4, formatting should take about 3-5 minutes, worst case, on a fast connection.  You are already using LVM, so I'd keep using it. Formatting a logical volume, LV, is seconds of clock time usually.

ext3 isn't bad for small disks, but ext4 is so much better, more reliable, faster.  You don't have a small disk.

/dev/mapper/ubuntu--vg-root: 464.3 GiB is way, way, way too big.  The root VG, which is where the OS gets stored should be 25G.  Create other LVs as needed for other uses, like /home/,  perhaps /var/lib/libvirt/ and perhaps /D1/ for generic data.

BTW, we NEVER, EVER, need to see loop devices in output.  Those just cruft up the important stuff, making it a hassle to help.

---

### Post by satimis on 2019-12-14
> **vanadium said:**
> By far the fastest way is to use mkfs, like you did. Why did you use ext3? ext4 is the current up to date format.

Also create a partition first.

AN alternative to using the command line for partitioning and formatting is to use the utility "Disks", which is by default installed on Ubuntu.
Hi,

Sorry it was a typing mistake.  It should be ext4..

I saw that it progressed slowly therefore I exited stopping it.

Only one partition.  I'll use the entire 4TB drive for storage only.  I ran fdisk creating the partition.  Ubuntu 18.04 is running on a 500G SSD drive.  Do I need creating 2 partitions?

satimis

---

### Post by satimis on 2019-12-14
> **Dennis N said:**
> I assume you intend to erase the existing Ubuntu? And Windows is not to be used?
```
sudo mkfs.ext3 /dev/sda
```
Without any partition? - this &#8593;  is not the correct way. You should always use partitions with Linux. To reuse a disk for Linux use, 1) create a new partition table on the disk - use GPT for type of partition table 2) create at least one partition and format the partition(s) ext4, not ext3. 

Hi,

ext3 was typing mistake.  It should be ext4

I ran fdisk creating ONE partition.  Do I need creating 2 partitions?  I'll use the entire 4TB WD drive for storage only.

> 
I suggest you use gparted from your existing install for these tasks, and avoid the terminal.
Whether you suggest using
--> Activities --> Disks (on top) ?

It took more than 10 hours to complete formatting the entire 4TB WD drive.  I learned a bitter lesson before.

Before posting I have tried again, the indication saying 13 hrs to complete.  Then I exited

satimis

---

### Post by satimis on 2019-12-14
> **TheFu said:**
> Always, always, partition a disk. ALWAYS!

Backup any data you want to keep.

Setup a GPT partition table. With 4TB, GPT is mandatory.

Setup any partitions. The size of those partitions should depend on how you will backup, restore, and use the partitions.
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) is my setup with reasons WHY.

If you use LVM and ext4, formatting should take about 3-5 minutes on a fast connection.  You are already using LVM, so I'd keep using it.

ext3 isn't bad for small disks, but ext4 is so much better, more reliable, faster.  You don't have a small disk.

/dev/mapper/ubuntu--vg-root: 464.3 GiB is way, way, way too big.  The root VG, which is where the OS gets stored should be 25G.  Create other LVs as needed for other uses, like /home/,  perhaps /var/lib/libvirt/ and perhaps /D1/ for generic data.

BTW, we NEVER, EVER, need to see loop devices in output.  Those just cruft up the important stuff, making it a hassle to help.
Hi,

There are no data on this 4TB WD drive.  

I ran fdisk creating ONE partition because I'll use the entire drive for storage only.  Ubuntu is running a 500G SSD,  Do I need to create 2 partitions?

# gdisk -l /dev/sda```

GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sda: 7814037168 sectors, 3.6 TiB
Model: HGST HUS726T4TAL
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 350C0B35-627B-44C2-AE9E-FF649B7FA72F
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7814037101 sectors (3.6 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

```

Other advice noted and thanks

Edit-1
=====
Will following article be relevant for running GPT ?
How to list, create, delete partitions on MBR and GPT disks - RHCSA Objective Preparation 
[https://linuxconfig.org/how-to-list-create-delete-partitions-on-mbr-and-gpt-disks-rhcsa-objective-preparation](https://linuxconfig.org/how-to-list-create-delete-partitions-on-mbr-and-gpt-disks-rhcsa-objective-preparation)

Edit-2
====
Edit-2
How to Format a Hard Drive Using Ubuntu
[https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu](https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu)

It'll take 13 hrs to complete formatting a 4TB WD drive

satimis

---

### Post by Dennis N on 2019-12-14
You need one partition only, but I would start out smaller - you can easily enlarge it later using the unallocated space after it. And you might later change your mind about just having one partition. The biggest disks I own are 1 TB and I've not made a partition bigger than my 250 GB data partition. I don't think it took more than a minute or so to format for LVM use. I use gparted for all such partitioning. I've never used gnome Disks for anything.

---

### Post by satimis on 2019-12-14
> **Dennis N said:**
> You need one partition only, but I would start out smaller - you can easily enlarge it later using the unallocated space after it. And you might later change your mind about just having one partition. The biggest disks I own are 1 TB and I've not made a partition bigger than my 250 GB data partition. I don't think it took more than a minute or so to format for LVM use. I use gparted for all such partitioning. I've never used gnome Disks for anything.
The total size of all data is exceeding 1TB.  Whether split them and store them on several partitions?

I have an external 2TB WD disk for storage.  It is nearly full.

satimis

---

### Post by Dennis N on 2019-12-14
> TThe total size of all data is exceeding 1TB. Whether split them and store them on several partitions?
If I had lots of existing folders with my files already organized, I would probably just make one partition big enough to hold all of them. But that's your decision to make.

---

### Post by satimis on 2019-12-15
Hi all,

Problem solved as follow;

Steps
1) install gparted

2) format 4TB WD drive according to following articles;
How to Format a Hard Drive Using Ubuntu
[https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu](https://www.wikihow.com/Format-a-Hard-Drive-Using-Ubuntu)
Method-2  Using GParted

# fdisk -l```

Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 343B80D3-E9CF-4B72-B4FF-2D311BA603E3

Device     Start        End    Sectors  Size Type
/dev/sda1   2048 7814035455 7814033408  3.7T Linux filesystem

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F3A8D40E-D988-4EF7-8FB7-B1F978474D92

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048   1050623   1048576   512M EFI System
/dev/sdb2  1050624 976771071 975720448 465.3G Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 464.3 GiB, 498539167744 bytes, 973709312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/ubuntu--vg-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Lot of thanks for your advice.

Regards
satimis


Regards
satimis

---

### Post by TheFu on 2019-12-15
That's 1-way.

Had you used LVM, then 1 partition, 1 pv, 1 vg, and any number of LVs could be used.  With LVM, moving all this data to other disk could be trivial.  LVM also provides nice ways to handle backups via snapshots.  Without LVM, you've just given up on that.  If the OS disk wasn't using LVM already, I wouldn't have written anything.  The system is already using LVM and already has the slightly added complication.  Not using it on new storage is a not-so-great idea, IMHO.

Haven't heard any mention of backups.  What's that plan?

---

### Post by satimis on 2019-12-15
> **TheFu said:**
> That's 1-way.

Had you used LVM, then 1 partition, 1 pv, 1 vg, and any number of LVs could be used.  With LVM, moving all this data to other disk could be trivial.  LVM also provides nice ways to handle backups via snapshots.  Without LVM, you've just given up on that.  If the OS disk wasn't using LVM already, I wouldn't have written anything.  The system is already using LVM and already has the slightly added complication.  Not using it on new storage is a not-so-great idea, IMHO.

Haven't heard any mention of backups.  What's that plan?
Hi,

I'll perform another test using the 500G Samsung SSD for data storage, creating LVM partition on it.  The same is now running Ubuntu 18.04 and I'll erase it.

This PC is originally having a m.2 pcie 1TB SSD running Ubuntu 18.04 desktop.

# fdisk -1 ```

....
Disk /dev/nvme0n1: 953.9 GiB, 1024209543168 bytes, 2000409264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 271E9246-CC54-4368-8693-FDCC3EE8AB23

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953.4G Linux LVM


Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 343B80D3-E9CF-4B72-B4FF-2D311BA603E3

Device     Start        End    Sectors  Size Type
/dev/sda1   2048 7814035455 7814033408  3.7T Linux filesystem

```

Please shed me some light how to proceed installing the LVM partition on the 500G Samsung SSD.

I don't keep backup.  I have an external 2TB WD drive keeping a duplicate copy of all data on the internal storage drive. 

Regards
satimis

---

### Post by Dennis N on 2019-12-15
> Please shed me some light how to proceed installing the LVM partition on the 500G Samsung SSD.
Shedding a bit of light: It's the same procedure as with the 4 tB drive, except when creating a partition using gparted, choose "Format as: LVM2 "
Also, before creating the LVM partition: if you plan to install an operating system, be sure to create a standard EFI system partition - usually as the first partition. 

Then you use terminal commands after that for creating a VG (volume group) and its LVs (logical volumes).
If you are not familiar with basic LVM management commands, you need to learn those. 
I used this tutorial as my first guide to LVM and its necessary management commands. 
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
Spend some time with it. Luckily it's still online! (Guide is apparently from 2012, but still good. It shows MSDOS partitioning - now we use GPT instead. But information on the management commands is still correct.)

---

### Post by TheFu on 2019-12-15
The link I posted above has my LVM layout.  The base partitions and LVs are good for an UEFI boot setup.  That disk is 500GB.  The /boot/, /boot/efi/ partitions and / LV is sized correctly.  All the other LVs are a matter of need, as described in the link.

Using LVM is about what you don't know tomorrow, not what you think you know about today.

There are tutorials for LVM.  Why did you choose it for the main OS if you didn't know about LVM already?
As already said, 
> Had you used LVM, then 1 partition, 1 pv, 1 vg, and any number of LVs could be used. 
A PV, Physical Volume, is 1-for-1 a partition.
A VG, Volume Group, is made of of 1 or more PVs.
LVs, Logical Volumes, are allocated/sized from a VG.  For day to day considerations, an LV is the same as a partition.  An LV gets formatted with a file system.  An LV is the unit where snapshots (lvm snapshots) are made.  When a snapshot is created, there must be sufficient storage in the VG to hold any data that changes for the life-time of the snapshot.

So with a 4tb PV/partition, I would use pvcreate, vgcreate, and lvcreate to make the PV, VG, then initial LV.
The most important part of using LVM is that increasing the size of any LV is trivial, reducing the size is a hassle.  A few of my rules:
* NEVER over-size/allocate an LV beyond what you can backup.
* Never have a VG span more than 1 physical disk, unless you have perfect backups or don't mind total data loss in the VG if 1 disk fails.
* Always leave plenty of storage for snapshots.

If the 2TB is for backups, then I wouldn't make the data LV on the 4TB disk over about 1.8TB in size.  Use the rest of the storage in a separate LV as scratch space.  Nothing wrong with scratch space, provided it disappearing in 5 minutes is ok.  Any disk can fail at any point.

For LVM knowledge, work through an LVM tutorial.  Before you've done anything else with the new disk is the best time to play.  Just be certain you don't accidentally play using the OS VG, LVs.  That could easily be bad.  Though you might enjoy using pvmove for fun.

What commands are part of LVM?  Use tab completion to discover some:
pv{tab}{tab}
vg{tab}{tab}
lv{tab}{tab}
For example:
```
$ vg{tab}{tab}
vgcfgbackup    vgconvert      vgextend       vgmknodes      vgs
vgcfgrestore   vgcreate       vgimport       vgreduce       vgscan
vgchange       vgdisplay      vgimportclone  vgremove       vgsplit
vgck           vgexport       vgmerge        vgrename
```

For an overview of all LVM storage on a system, use:
```
sudo pvs
sudo vgs
sudo lvs
```
There aren't any GUI tools for LVM.  Pretty much any tutorial from any Linux found using any search engine will be fine.  LVM is LVM is LVM regardless of the distro or release.  Basic use only uses a few of those commands.

---

### Post by TheFu on 2019-12-16
Formatted a few LVs on an 8TB, usb3 connected, disk today.
```
$ time sudo mkfs -t ext4 /dev/mapper/istar--8TB--vg5-istar--lv5 
mke2fs 1.42.13 (17-May-2015)
Creating filesystem with 805306368 4k blocks and 201326592 inodes
Filesystem UUID: 7dc085ef-9b09-4dea-ba91-dd60f10e7417
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000, 214990848, 512000000, 550731776, 644972544

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done       

**real    0m4.398s**
user    0m0.144s
sys     0m0.224s

lsblk  .... 
sdg                                   7.3T disk             
&#9500;&#9472;sdg1                                3.7T part LVM2_member 
&#9474; &#9492;&#9472;istar--8TB--vg4-istar--lv4          3T lvm  ext4        
&#9492;&#9472;sdg2                                3.7T part LVM2_member 
  &#9492;&#9472;istar--8TB--vg5-istar--lv5          3T lvm  ext4        

```

Wall clock time was under 5 seconds.  The system involved is my lowest-end, 5+ yr old, dual-core Pentium box.
I've only allocated 3TB per LV. Room to grow, room for snapshots, and for future unknown needs.
The 2nd LV took about the same wall time.

Anyways, the point is that formatting almost any size ext4 file system on an LV managed by LVM is a trivial operation. If it isn't this fast there, I think something else is wrong.

---

