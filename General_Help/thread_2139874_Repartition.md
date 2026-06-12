---
title: "Repartition"
date: 2013-04-28
forum: General Help
---

### Post by arkyub23 on 2013-04-28
I need help, guys.
I dont know how to repartition. I'm a newbie here.
I got this kind of warning, "The partition is misaligned by 1024bytes. This mat result in very poor performance. Repartitioning is suggested.

Thanks :)

---

### Post by fantab on 2013-04-28
Can you tell us what OS you are using and in what Version? Is it the HDD you want to partition or SSD? How Big is your Disk?

If you have any DATA to save from the disk, please do so before you proceed.

---

### Post by arkyub23 on 2013-04-28
I use Ubuntu 12.04. 
I will be partitioning an HDD about 322GB.
I already backed up data.

Thanks

---

### Post by fantab on 2013-04-28
I am asuming that you are not dual-booting:

Boot with your Ubuntu installation Disk and choose to "**TRY UBUNTU**". Once you have a working Desktop open utility called '**DISKS**'; clik on the gear-like icon and Run **SMART** tests on your HDD. It will run those tests and will tell you if your HDD is "healthy" or not. If its not healthy then you must replace the HDD or repair it.

If its Healthy then: close Disks and open **GPARTED**. Delete all partitions and 'apply'. From Gparted Menu Bar select 'Devices' -> **Create Partition Table**: choose **MS-DOS**, which is default, 'apply'.

Then you will create partitions or install Ubuntu. If you install Ubuntu it create partitions of default size and install. If you want to manually control the disk space then you can Create partitions using Gparted: and when installing Ubuntu choose "**SOMETHING ELSE**" Option.

Here's how I would do it:
1st partition /dev/sda1 PRIMARY 20-25GB ext4 (During Install you will use "/" mountpoint)
/dev/sda2 PRIMARY 20-25GB ext4 (Leave it free so you can either install another version/flavor of Ubuntu or another Distro)
/dev/sda3 PRIMARY 20-25GB ext4 (Leave it free so you can either install another version/flavor of Ubuntu or another Distro)
/dev/sda4 EXTENDED all the remaining GB.
/dev/sda5 LOGICAL 2-4GB SWAP
/dev/sda6 LOGICAL remainingGB ext4 (We will use this to store DATA)

OR
/dev/sda1 PRIMARY ext4 20-25GB (during Ubuntu install use "/" as mountpoint)
/dev/sda2 PRIMARY SWAP 2-4GB
/dev/sda3 PRIMARY ext4 remainingGB (during Ubuntu install use "/home" as mountpoint)

Good Luck...

---

### Post by arkyub23 on 2013-04-28
yes im not dual-booting.

does this mean I will format my pc?
only my logical partition is misaligned.. the one that I use to store data..

---

### Post by fantab on 2013-04-28
Yes you will reformat all your HDD.
I guess you can fix your misaligned partition. But I don't know how well that will solve the issue. Repartitioning should be the way to go about it.
Since you have your DATA Backed up, this can be a good opportunity to re-create partitions they way you really want them.

EDIT: also check in your BIOS what SATA mode its using: IDE, RAID or AHCI. AHCI should be set, if its not. It communicates better with SATA HDD.

Read this Thread: [http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018) it has some info about misaligned partitions. This too: [http://askubuntu.com/questions/134023/file-system-is-not-clean-the-partition-is-misaligned-by-1024-bytes](http://askubuntu.com/questions/134023/file-system-is-not-clean-the-partition-is-misaligned-by-1024-bytes)

You can also search www for more info.

---

