---
title: "how can i use the bulk of my 500gb drive as /home"
date: 2018-11-20
forum: General Help
---

### Post by pjstock on 2018-11-20
I've had 16.04 installed on a laptop for a while (dual with Windows) but I think when I installed a made two errors.
1) I don't seem to have "enabled" the bulk of my 500gb HDD. and 
2) I expect in having not done that and speced it as /home, my /home is on the 40gb boot partition.

This is a little used laptop and so this hasn't been a problem to date. But it might start to gum things up eventually. 4

How can I move my /home to sda2 (418GB partition) and make it so that Ubuntu recognizes and can use it?
or what have I done?
Peter

```
peter@peter-ThinkPad-T420:~$ sudo fdisk -l
[sudo] password for peter: 
Disk /dev/loop0: 8.6 MiB, 9023488 bytes, 17624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 87.9 MiB, 92114944 bytes, 179912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 45.3 MiB, 47456256 bytes, 92688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 87.9 MiB, 92119040 bytes, 179920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 128.3 MiB, 134565888 bytes, 262824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 45.3 MiB, 47456256 bytes, 92688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xcd5cd326

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 877956489 877749642 418.6G  7 HPFS/NTFS/exFAT
/dev/sda3       877957118 976771071  98813954  47.1G  5 Extended
/dev/sda5       877957120 960235519  82278400  39.2G 83 Linux
/dev/sda6       960237568 976771071  16533504   7.9G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.


```

---

### Post by oldos2er on 2018-11-20
See [https://askubuntu.com/questions/643441/how-to-create-a-separate-home-partition-after-installing-ubuntu-under-single-p](https://askubuntu.com/questions/643441/how-to-create-a-separate-home-partition-after-installing-ubuntu-under-single-p)

---

### Post by TheFu on 2018-11-20
You cannot use NTFS formatted storage as HOME.

BTW, all the "loop" devices in the fdisk output are useless. They are for snaps and totally irrelevant.
And the fact that sda3 doesn't start on a sector boundary can slow performance 10-30% for accessing this disk.  Partitions need to be on 4096b boundaries.

So, there are 50 different solutions to the issue you have.  Which makes the most sense depends on whether any data in each partition is to be saved or not.  But, in general, it goes like this:
* backup any data you cannot lose onto other storage.
* Using a live-boot Ubuntu, run **gparted**
* With gparted, 
** wipe this disk (or just delete everything on it - data, partitions, partition table, 
** create a GPT partition table (not MBR), since you can now. It is easier now and much more flexible.
* Consider using LVM2 if this disk will be for Linux-only use.
* Create 2 partitions, one at the front of the disk, the other at the end of the disk.  Size them for the needs you have.  The plan would be to leave some space in the middle unused.  If you choose to use LVM2, then you can make 1 huge partition for all the storage, since LVM allows resizing of partitions, as needed, usually on a running systems. No reboot needed. LVM is very powerful.

If you want to try out LVM, before you have any important data on the disk, play around with the PEs, VGs, LVs, and mounting the LVs.  Learn it now, when you don't have data at risk.  Out side of LVM administration, an LV can be considered a disk partition.  This is also the time to consider using LUKS encryption.

For example:
```
$ lsblk
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
&#9500;&#9472;sda2                          8:2    0  488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0 54.9G  0 part  
&#9474; &#9492;&#9472;sda3_crypt                253:0    0 54.9G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root   253:1    0   51G  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1 253:2    0  3.9G  0 lvm   [SWAP]
&#9492;&#9472;sda1                          8:1    0  512M  0 part  /boot/efi
```
You can see from above that sda3 is a partition that holds an encrypted container, which holds both / and swap LVs.  /boot/ and /boot/efi are outside the encrypted areas in sda1 and sda2.  It is possible to resize anything held inside the sda3_crypt container using LVM commands.  Resizing sda3_crypt or sda3 would require effectively wiping the disk, but if sda3 was a partition that completely filled the disk (say it was a 340G disk), then there would be some extreme flexibility possible.
I show the /boot and /boot/efi only for completeness. For a /home/ only disk, I'd use 1 large partition and setup LVM with a 100G /home LV.  The entire partition would be in a single PV and the VG would hold all of it too.  Then I'd add storage as needed to the LV or perhaps make other LVs for other purposes.

Whenever I setup storage, how it will be backed up is the 2nd thing I consider.  I have a few 4TB and 8TB disks, but to make my backups easier, I never allow any LV to be larger than 4TB.

---

### Post by pjstock on 2018-11-20
I would just wipe the disk, but I would like to hang onto the Windows 7 OS install (even though I rarely use it, recently I have had to switch to it to play a DVD for instance when Ubuntu would not. That's another issue). wouldn't your suggestion wipe out my Windows? 
Am I correct that I have most of the drive (sda2) dedicated to WIndows boot and data, 419gb? If so, that's WAAAAY overkill. I would happily reduce that.

can I used Gparted to reduce that and then allocate the excess to a partition I would used for /home (as what? EXT?)
Or do I have to Shrink Windows in using diskmanagement in WIndows ?

and Ultimate Stupid question but how do I square what I see reported by fdisk with what I see on my destop?

on the desktop I "see":
449gb Vol (which appears to be 449gb in size)
and my /home which in Properties appears to be 14gb (10.5 used, 3.5 free)

what does these correspond to in terms of: sda2 (419GB NTFS), sda3 (47.1gb EXTended) , sda5 (39.2GB Linux),.... oh wait a minute. sda3 seems to be the total of sda5 (39gb) and sda6 (the 7.xGB swap)

so the one I don't understand is the 449 GB Vol I see on my desktop, under Computer.
and why is "home" (on the desktop) restricted to 14gb?

---

### Post by TheFu on 2018-11-20
Basically, the current setup is great, until you want to change it.

I'm not a Windows person, but used to be long ago. I've always suggested that managing the partitions should be done using the OS that the partition is mainly used by. Changing partitions for any OS can make that OS unbootable, so be prepared if that happens.

Sorry about all the LVM stuff. I assumed you had more expertise than you do. Probably best to ignore all of that.  Also, if you need to keep Windows, then you might not be able to move to GPT.  That's unfortunate since GPT solves many limitations with MBR/MSDOS partition tables.  But we've lived with those for 30+ yrs, so what's a few more?

fdisk is telling the truth.  Any desktop programs are "simplifying" things. This is the important part:
```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 877956489 877749642 418.6G  7 HPFS/NTFS/exFAT
/dev/sda3       877957118 976771071  98813954  47.1G  5 Extended
/dev/sda5       877957120 960235519  82278400  39.2G 83 Linux
/dev/sda6       960237568 976771071  16533504   7.9G 82 Linux swap / Solaris
```
sda3 is an "extended partition".  You can look that up in wikipedia.  Any partition with a number of 5 or height is/must be completely contained inside this extended partition.
Gaining access to the 418G of storage in sda2 will be non-trivial because you will have to reduce sda2, then remove sda5 and sda6 before you can modify sda3 at all.  The easiest answer would be to buy a 1TB external disk for $45, move everything over to it (using a bit-for-bit cloning tool), then wipe the 500G disk, reinstall Windows, reduce the size to 100G or so, then install Ubuntu.  

If you do choose to do anything, please, please, make a 100% know-you-can-restore backup. People unfamiliar with partitioning tend to make catastrophic mistakes and lose lots of data. By swapping in a new HDD, the risks are effectively gone and you can try things without worry.  Just be certain that the current disk is not connected to the computer in any way first.

---

### Post by samuelfcapbell1 on 2018-11-20
Interesting output you have there! I was just reading up on using the **G Parted GNOME Partition editor**, for creating, _reorganizing_, and _deleting disk partitions_. 

Caution
Editing partitions has the potential to cause LOSS of DATA. 
The G Parted application is designed to enable you to edit partitions while reducing the risk of data loss. The application is carefully tested and is used by the GParted project team. However, loss of data might occur due to software bugs, hardware problems, or power failure. 
You can help to reduce the risk of data loss by not mounting or unmounting partitions outside of the G Parted application while G Parted is running. 
You are advised to BACKUP your DATA before using the G Parted application. This is especially true for encrypted data where all of the data can become permanently inaccessible after a failure. Please refer to The Cryptsetup FAQ for backup and recovery advice of encrypted data.

Well to make a long story short: I would consider backing any data you have on that 500 GB device. Then remove all data and properly re-partition your drive following the G Parted User Guide. You may not learn as much as trying to sort through what you have created. It seems your output is showing you have way too many small devices. ie. msdos partition table limits maybe. 

I used to work as a volunteer tech at a computer ministry recycling computers for the low-income single mothers so they could have something help them with job search and assist them with a sort of digital babysitter and old computer with a good Operating system the basic games and the bible etc... And there were so many different types of repair requests. Most of the time rather than trying to trace down what went wrong it was quicker to just salvage the info and start a-new. Easier said when you have a room full of just old hard drives another plus renting a few storage boxes full of old terminals and keyboards and recycled parts a lot of folks would call garbage to work with. You don't have those luxuries working and learning on your own. 

There's another lesson I walked away with. Dual boot is a crazy cool idea. However the Windows side may be more vulnerable than the Linux side. If the machine gets infected through the Windows side both are down. Other wise a lot of the cool Linux do it your self and fix it approach to computers and life seem to be based on a Linux host machine just to be on the safe side for example **Creating a New Partition Table you might want to**, sort of giving **root** the actual and real bottom line! there by not blocking or hindering functions like Data Rescue, **Refreshing your devices** or path operations of File System Support, **Mounting** and **Unmounting Partitions, ****Creating a New or****Deleting a Partition, **msdos, primary partitions, extended partitions, maximun partitions allowed on a disk device depending. [B][I]With G Parted as your go to _Partition editing tool_ your solution might be as simple as a cut and/or copy/paste! 

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)[/I][/B]

---

### Post by TheFu on 2018-11-20
>  It seems your output is showing you have way too many small devices. 

That isn't what the fdisk output is showing.  All the loop devices are showing that snap packages are being used. Nothing more. They mean ZERO, nada, nothing, to storage.

---

### Post by pjstock on 2018-11-20
No, for all the time I've spent installing and using Ubuntu as a work tool - 15 years? - i am really not very savvy technically. (Thougj I am.learning a lot his week tryng to trouble shoot.three systems)

But I would never figure out LVM

Fortunately this laptop get a very little use (it's more if a browsing ng tool while travelling, or a workstation onto which I copy batches of files I have to work on or edit). But there is nothing on it I really need. (Nonetheless I'll review it's.contents and backup anything interesting)

The real "problem." Is that Windows, while only used once in a blue.moon, comes preinstalled on these machines and so If somethg goes wrong, you don't even have the ability to restall.

Maybe I just bite the bullet, finally turn my back on Windows completely and just say Hello Ubuntu 1000%.  I really cant think of task i have not been able.to.do in Ubuntu. (Except.for that darn dvd that wouldn't play last weekend in Ubuntu but did play in Windows.)

---

### Post by TheFu on 2018-11-20
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) explains how to playback DRM DVDs.

But Windows has a built-in way to make an install disk.  LMGT: [https://www.microsoft.com/en-us/software-download/windows7](https://www.microsoft.com/en-us/software-download/windows7) there are lots of guides and videos to do it.

---

### Post by pjstock on 2018-11-21
OK, I am tryingt. I am REALLY trying. but this moving /home is not going very smoothly.

I am trying to follow the turorials and I have I think done step 1, creating a new partition.(after shrinking the Windows partition)
this is what I have now:
```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 143568265 143361418  68.4G  7 HPFS/NTFS/exFAT
/dev/sda3       877957118 976771071  98813954  47.1G  5 Extended
/dev/sda4       143568896 877955071 734386176 350.2G 83 Linux
/dev/sda5       877957120 960235519  82278400  39.2G 83 Linux
/dev/sda6       960237568 976771071  16533504   7.9G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.

```

But the next step of the tutorial says:

```
Copy Home Files to New Partition : copy your files from old home to the newly created partition

sudo cp -Rp /home/* /new-partition-mount-point

```

1. How do I know what to specify for the "new-partition-mount-point"?

Next. Fdisk is telling me:
Partition 3 does not start on physical sector boundary.

I understand that I have to move or resize that partition so that it does start where it should. But that partition sda3 is locked. (I am in Live Boot mode off a USB stick)
How do I get access to that partition to move it?

Next. I am also seeing "Partition table entries are not in disk order."
though I also read that this is not a big deal or a problem. 
can I leave it as is? (the correcting steps seem complicated, at least to me.)

---

### Post by TheFu on 2018-11-21
> **pjstock said:**
> OK, I am tryingt. I am REALLY trying. but this moving /home is not going very smoothly.

I am trying to follow the turorials and I have I think done step 1, creating a new partition.(after shrinking the Windows partition)
this is what I have now:
```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 143568265 143361418  68.4G  7 HPFS/NTFS/exFAT
/dev/sda3       877957118 976771071  98813954  47.1G  5 Extended
/dev/sda4       143568896 877955071 734386176 350.2G 83 Linux
/dev/sda5       877957120 960235519  82278400  39.2G 83 Linux
/dev/sda6       960237568 976771071  16533504   7.9G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.

```

But the next step of the tutorial says:

```
Copy Home Files to New Partition : copy your files from old home to the newly created partition

sudo cp -Rp /home/* /new-partition-mount-point

```

1. How do I know what to specify for the "new-partition-mount-point"?



A mount point is just an empty directory where you mount storage.  Make one. It isn't automatic. For temporary needs, like this, I'd use /mnt/ ... so 
```
sudo mount /dev/sda4    /mnt
``` I'm assuming you have already formatted the file system pre-mounting.  Ext4 would be a reasonable choice.  

Later, you will mount it to /home/.

Of course, you could move /home on the old partition to /home-old, then mkdir /home and ```
sudo mount /dev/sda4    /home
``` before moving all the files.  Move/copy, shouldn't matter.

---

### Post by TheFu on 2018-11-21
> **pjstock said:**
> Next. Fdisk is telling me:
Partition 3 does not start on physical sector boundary.

I understand that I have to move or resize that partition so that it does start where it should. But that partition sda3 is locked. (I am in Live Boot mode off a USB stick)
How do I get access to that partition to move it?

To do anything with sda3, you'll need to remove sda5-sda99.  Thought I'd said that above. Maybe I wasn't clear. Sorry.

---

### Post by TheFu on 2018-11-21
> **pjstock said:**
> Next. I am also seeing "Partition table entries are not in disk order."
though I also read that this is not a big deal or a problem. 
can I leave it as is? (the correcting steps seem complicated, at least to me.)

Not much you can easily do, without buying a new HDD and doing a few reinstalls.  It isn't important at all.

---

