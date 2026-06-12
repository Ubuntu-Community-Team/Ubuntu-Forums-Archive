---
title: "Help with GParted"
date: 2021-09-24
forum: General Help
---

### Post by arthurconmy on 2021-09-24
Hello, I'm trying to increase the partition size of `/dev/sda5` by the unallocated bit shown.



However, I don't seem to be able to do this since it's currently mounted (I think). Is it possible to do so?

---

### Post by Holger_Gehrke on 2021-09-24
Look at the mount point of sda5. sda5 is mounted as the root of your file system tree. You can't unmount the root - you wouldn't have a filesystem left. You have to boot a live system and run gparted from that to manipulate /dev/sda5 (or whatever name it gets when booting from a live system ...).

Holger

---

### Post by &amp;KyT$0P# on 2021-09-24
Yes.  You will need to boot from a live USB to do it though as you cannot make these type of modifications to a running system.

* oops, Holger_Gehrke beat me to it

---

### Post by arthurconmy on 2021-09-24
Ah ok - so load e.g Ubuntu onto a USB and then run GParted from within that?

---

### Post by monkeybrain20122 on 2021-09-24
> **arthurconmy said:**
> Ah ok - so load e.g Ubuntu onto a USB and then run GParted from within that?

Boot off a Ubuntu live usb, start gparted, in 'device' choose your internal hard drive, unmount  sda4 (the extended partition) and sda5, then expand first sda4 then sda5 to the unallocated space. But be warned that extending/moving to the  left might be problematic and your system may got destroyed as a result. Extending to the right, on the other hand, is quite safe, have done it many times. Your layout is kind of odd.

an alternative way is to clone your sda5 with fsarchiver, then delete sda4 and sda5 from gparted (from live usb) and then create a new partition that include the unallocated space and restore your image to it.

---

### Post by grahammechanical on 2021-09-24
My advice is to do one action at a time. Some of these actions take a long time to complete. A list of actions will take a very long time to complete. I get nervous waiting and wondering. So, I do one action at a time. There will be warning notices that are scary but things usually complete satisfactory.

Regards

---

### Post by TheFu on 2021-09-24
Because the partition table is a legacy style, *MBR*, you have a "*logical partition*" for Linux. This is wholly contained within sda4, which is the "*Extended Primary Partition*".  The free space is outside sda4.  This will cause problems.

It appears this is a dual-boot system, which causes even more issues.  If it wasn't, I'd say to convert the *MBR* to *GPT*, which would remove the entire "*logical partition*" trap you (and some of us too) have.

Before doing anything, before touching any partitions, be 100% certain you have a perfect, restorable, backup of **everything** on the disk, not just the linux stuff, but all the Windows stuff too.  Anything you don't want to lose needs to be in that backup.  If you don't have a backup, this would be an excellent time to buy a replacement HDD and create a GPT partition, then move each of the partitions over using **fsarchiver** FROM the old disk TO the new disk.  This would, in effect, create and test your ability to clone storage at the partition level and to fix the resulting issues after the fact with next to zero risks. If anything bad happens or you can't figure out how to get Windows or Linux to boot on the new disk, just swap the old HDD back in.

Avoid *MBR* and choose *GPT*. There are many reasons, many upsides, no downsides once the move is completed. It is only the move that can be challenging.  I think Win7 and later support GPT, assuming 64-bit and UEFI booting. Linux doesn't care. It supports GPT, period.  No more need for logical partitions and no 4 primary partition limits.  The new limit is 128 primary partitions - which isn't really any limit.  A long time ago, I had a mission to see how many OSes I could get onto a single drive, for fun.  Got to 50 - each with a different partition. They all worked.

What version of Windows fits into less than 60G of storage?  The last time I saw that was with WinXP.  If it is just data and the only OS on the system is Linux, best to convert that into a native Linux data partition too.  Performance will be better and sharing over the network works easier.

For any terms that are unfamiliar, wikipedia has articles, which can explain clearly.

---

### Post by arthurconmy on 2021-09-25
> **TheFu said:**
> Because the partition table is a legacy style, *MBR*, you have a "*logical partition*" for Linux. This is wholly contained within sda4, which is the "*Extended Primary Partition*".  The free space is outside sda4.  This will cause problems.

It appears this is a dual-boot system, which causes even more issues.  If it wasn't, I'd say to convert the *MBR* to *GPT*, which would remove the entire "*logical partition*" trap you (and some of us too) have.

Before doing anything, before touching any partitions, be 100% certain you have a perfect, restorable, backup of **everything** on the disk, not just the linux stuff, but all the Windows stuff too.  Anything you don't want to lose needs to be in that backup.  If you don't have a backup, this would be an excellent time to buy a replacement HDD and create a GPT partition, then move each of the partitions over using **fsarchiver** FROM the old disk TO the new disk.  This would, in effect, create and test your ability to clone storage at the partition level and to fix the resulting issues after the fact with next to zero risks. If anything bad happens or you can't figure out how to get Windows or Linux to boot on the new disk, just swap the old HDD back in.

Avoid *MBR* and choose *GPT*. There are many reasons, many upsides, no downsides once the move is completed. It is only the move that can be challenging.  I think Win7 and later support GPT, assuming 64-bit and UEFI booting. Linux doesn't care. It supports GPT, period.  No more need for logical partitions and no 4 primary partition limits.  The new limit is 128 primary partitions - which isn't really any limit.  A long time ago, I had a mission to see how many OSes I could get onto a single drive, for fun.  Got to 50 - each with a different partition. They all worked.

What version of Windows fits into less than 60G of storage?  The last time I saw that was with WinXP.  If it is just data and the only OS on the system is Linux, best to convert that into a native Linux data partition too.  Performance will be better and sharing over the network works easier.

For any terms that are unfamiliar, wikipedia has articles, which can explain clearly.

Thanks so much for this.

For more detail yeah, originally the laptop was on Windows 10 and I am dual booting. However, I have no use of the windows any more. 

I think I managed to make the linux partition with an external drive but should have definitely made a bigger partition. The view shown in GParted was done by reducing the windows partition size.

Is there a better solution to get more space for linux than the above mentioned external drive way? Important points: the computer has no valuable data, and the windows partition is useless to me.

---

### Post by tea for one on 2021-09-25
> **arthurconmy said:**
> Is there a better solution to get more space for linux than the above mentioned external drive way? Important points: the computer has no valuable data, and the windows partition is useless to me.

Indeed, there is.
Install your preferred Ubuntu flavour from scratch and let the installer choose the partitions.
Windows 10 will be removed and you will have full use of the disk.

Don't forget to boot in UEFI mode.
When you reach a live session, open up gparted > Device > Partition Table > GPT (this is the modern partition table)

---

### Post by TheFu on 2021-09-25
> **arthurconmy said:**
>  <snip>
I think I managed to make the linux partition with an external drive but should have definitely made a bigger partition. The view shown in GParted was done by reducing the windows partition size.

Is there a better solution to get more space for linux than the above mentioned external drive way? Important points: the computer has no valuable data, and the windows partition is useless to me.

Please be certain you are using terms correctly.  _Drive_ is not the same as _Partition_.  Almost always, Windows has been lying to people by calling C: and D: "drives." - that is factually incorrect and leads to much confusion. A few days ago, I wrote a long post about partitions and mounting them and choosing file systems.  Maybe search for that?  

Here's another one: [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)

If you can, and truly don't care about the data, the best, easiest answer, would be to do a reinstall and let Ubuntu take over the entire drive.  If it were me, I'd want to ensure that 

[LIST]
[*]/ (the root partition) is only 35G. The size is to make backups and cloning easier.
[*]swap partition is 4.1G.  I use a partition, not file and I don't hibernate, ever.
[*]/home is a partition, probably 50G per user.  Also important for backups to limit this size.
[*]/stuff is a partition, using ~80% of the total storage on the device.  /stuff don't get backed up, ever. Data there is temporary and stored elsewhere.
[*]I leave 20% of the storage unused. This is for "future needs" that I can't predict.

[/LIST]
On some systems, like my travel laptop, I'm using about 50% of the storage. I just don't need any more, so why not let the SSD have a little room to do wear leveling?  

Ok, I lied.  I don't really use partitions.  I use LVM and logical volumes. These are crazy flexible and have been enterprise storage management tools for 30 yrs.  They have some complexity that non-admin users wouldn't want.  Basically, an LVM-LV can be considered a "partition" for all the good stuff, but has the flexibility that normal partitions lack.

If you are tempted to use BTRFS, please don't.  Go read this article: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/) first.  Have your eyes open.  Basically, he suggests 2, very specific uses for btrfs.

If I were setting up a new system for data, I'd use ZFS for the data areas only.  I wouldn't use ZFS for /home or / or anything related to booting ... just for data.  

I choose to use LVM for / and /home, but again, I'm comfortable with LVM and the complexity.  ZFS will blow your mind, if you don't have an enterprise storage background.

---

