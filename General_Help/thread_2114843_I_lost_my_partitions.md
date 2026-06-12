---
title: "I lost my partitions"
date: 2013-02-11
forum: General Help
---

### Post by Black Vise on 2013-02-11
Hi,
I'm a newbie in Linux and Xubuntu, and I messed my laptop.

Yesterday I tried to dual boot Win 7 32-bit and latest Xubuntu, I install Xubuntu using unetbootin USB Flash Drive. And now all the Win 7 partitions is missing, I really hope the files was preserved because I only did a quick documents backup.

Before I started install Xubuntu, in Win 7 I have 4 Partition iin 500GB HD, C:120GB; D:120GB;  E:140GB;  F:140GB.
I then shrink some using Win 7 Disk Manager to create new partition  for Xubuntu and the Swap. it now became
X:20GB; C:100GB; S:5GB; D:125GB; E:130GB; and F: 140GB

Then I run Xubuntu install and format X as ext3 and S as swap, at the first installation  I can't install grub at any sda, so I skipped it,  at the first boot I met "Missing operating system" screen.

 I reinstall Xubuntu again, but this time no problem with grub, but I still can't pass the "Missing operating system".
Using the live USB Flash Drive I installed and run Boot Repair, and repair MBR.

Then I reinstall Xubuntu, this time I didn't see any other partition besides X: S: and about 360GB unknown partition. I used the default partition, which I think it removed win 7, since in the installation window says " removing other operating systems".

This installation is success, I can enter Xubuntu but my other partition is still missing, GParted screenshot below.

[[IMG]http://www1.picturepush.com/photo/a/12165099/220/12165099.png[/IMG]]("http://picturepush.com/public/12165099")

 So what should I do in order to recover my files and partitions? 
I've run Win 7 Recovery CD and it can't find my WIn 7 installation, should I reinstall Win 7? 

Thanks in advance and sorry for my bad english.:KS
Black Vise

---

### Post by Impavidus on 2013-02-11
If I understand correctly, win7 32-bit doesn't support UEFI. Without UEFI Windows doesn't support GPT partitioning, leading to the conclusion that your hard disk uses MBR partitioning. So, you have a limit of four primary partitions on your disk.

The question now is: Which of your original partitions were primary and which were logical? (Please answer.)

Your xubuntu root and swap partitions are primary, and so was your windows C partition (as windows requires it to be primary), so this could only have worked if your D, E and F partitions were in an extended partition at the start of the disk. Else, windows converted your partitions to dynamic, which is not understood by linux, explaining the complete mess you got into.

The original D, E and F partitions are inside the unknown partition, the original C partition is in the first unallocated block. Recovery may still be possible, but I'm glad you made at least back-ups of your documents.

---

### Post by oldfred on 2013-02-11
Or did you let Windows convert to dynamic partitioning which does not work with Linux. It does seem they are improving the support as it may now at least see a drive with dynamic partitions.

Post this:

sudo fdisk -lu

If any partition is shown as SFS not NTFS then you have dynamic partitions, the NTFS partition is a logical partition inside the SFS. It is somewhat similar to LVM in Linux.

---

### Post by Black Vise on 2013-02-11
Hi Impavidus and oldfred

Impavidus I think you're right, all of my partitions seems to be primary and it's very likely that the X and S drive are dynamic. 

oldfred, here's the result of sudo fdisk -lu

```

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x421067d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   719448063   359724000+  42  SFS
Partition 1 does not start on physical sector boundary.
/dev/sda2       719448064   729688063     5120000   82  Linux swap / Solaris
/dev/sda3   *   935811072   976771119    20480024   83  Linux

```

---

### Post by oldfred on 2013-02-11
Microsoft's offical policy is to totally backup, delete everything, repartition and restore data. But some third party tools may work, but I think it only works if you have only 4 or less partitions so it can convert to primary.

Of course whatever you do backup is most important as these are major partition changes.

       Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 


This is a new issue with left over data on hard drive.

GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

### Post by Black Vise on 2013-02-11
Wow thanks a lot oldfred, but I really don't have a clue, 
So I will be able to mount and read my files in missing partitions if I convert 360GB unknown into basic, is that right?
[SIZE=2]I'll try Partition Wizard 4.2 Free at Boot[/SIZE], is there any better solution with higher chance to recover files?

---

### Post by Mark Phelps on 2013-02-11
I don't think the Free version of Minitool Partition Wizard (now known as the HOME version) does the dynamic-to-basic conversion anymore.  I know the Pro version does, but you have to pay for that.

---

### Post by Black Vise on 2013-02-12
Hi Mark, yes I believe so, Partition Master is also need at least paid Professional Edition to be able to create PE cd.

Today I've tried TestDisk, using the Deep Search twice and I still can't continue to convert any partitions, I'm stuck.

Is there any other tools on linux or boot to convert dynamic to basic partition with higher chance of file recovery?

---

