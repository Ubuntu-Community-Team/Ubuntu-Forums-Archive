---
title: "dual boot on HP Compaq with Win 10, &quot;installation type&quot; menu choices"
date: 2017-09-09
forum: General Help
---

### Post by kell2 on 2017-09-09
I have a PC that runs Windows 10, and I would like to install Ubuntu to dual boot.  I created a partition on  the PC's hard disk, and made a live usb.  The new partition on the PC  is formatted ntfs.  I'm running Ubuntu from the live usb and navigating  the installation menu right now.

The first popup asked me if I want to unmount /dev/sdb.  I chose no.

Now I'm looking at the "Installation type" box.  I assume I should format the new partition in Ext4, so
In the list of devices I choose the new partition /dev/sda4
Edit partition
Use as: Ext4 journaling file system
Format the partition:

and now I have to choose the mount point,
/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local

Also, at the bottom of the "Installation type" box is 
Device for boot loader installation:
/dev/sda ATA ST3160318AS(160.0GB)
/dev/sda1 Windows 10 (loader)
/dev/sda2
/dev/sda3
/dev/sda4
/dev/sdb JetFlash Transcend 8GB (8.0 GB)
/dev/sdb1

Assuming my choices not to unmount the usb and to format the new  partition are appropriate (correct me if I'm wrong), then my question is

what do I choose for 
1 mount point, and 
2 Device for boot loader installation

---

### Post by oldfred on 2017-09-09
You have to have / (root).
Default install of 16.04 have just / & swap. 
Some like to make /home a separate partition or have data in another partition than the operating system. Back with XP I did that with a separate NTFS data partition which then when I first installed Ubuntu used as a shared data partition.
Other partitions are primarily for servers or very advanced users that want specific data on different drives/partitions.

With 17.04 and later a swap file is used unless a swap partition already exists.
If you have 4GB of RAM or more you may not use swap unless editing videos and those users add huge amounts of RAM so as not to use swap as it is slow.

You always install grub2's boot loader to a drive like sda or sdb, (almost) never to a partition.
But if UEFI, it really does not matter what you choose as grub will install boot files into the ESP - efi system partition on drive seen as sda. 
Windows & Ubuntu will share the ESP with different folders.

For more info on UEFI installs see link below in my signature.

For HP/Compaq you may need one of the several alternative work arounds to boot in UEFI mode.
HP violates UEFI spec that says NOT to use UEFI description as part of boot and only valid description is "Windows Boot Manager".

---

### Post by kell2 on 2017-09-09
I got the installation done.  How do I mark this thread solved?

---

### Post by oldfred on 2017-09-09
Quick answer in my signature.

details:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

