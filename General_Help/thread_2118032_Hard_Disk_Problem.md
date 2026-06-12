---
title: "Hard Disk Problem"
date: 2013-02-20
forum: General Help
---

### Post by avsksan on 2013-02-20
Hai everybody,
           I am a new to linux community but a regular user of computer. I just bought a Laptop for my regular use. In that i made a mistake that during installing windows 7, i parted the disk into 3 partitions( during installation) and re adjusted in to 5 parts using windows disk management. Now the problem is that i could not able to install ubunto 12.04 lts due tot he disk partition i made the ubunto say i have three partitions while i really have 5 parts in windows. How can get out of it? can i clear from all of this and make the hard disk as i bought or tis there any other way than installing in virtual box. Please help me
thank you in advance,

---

### Post by aarons6 on 2013-02-20
when ubuntu asks to what drive you want to install it to, just choose advanced.

you can then delete and add partitions as you want.
you need at least one / partition that is ext4.. around 30gb is good.
the next is optional.
you can have a separate one that is /home as big as you want, this will keep your files. id put atleast 100gb, everything you download, pictures, music, games installed with wine will go here.

then finally you need one swap partition.. around 1 to 2gb is a good amount.

keeping the partitions separate makes installing dist updates easier.. as its always best to reinstall when going up instead of just upgrading.

you wont want to reformat your /home partition each time..

---

### Post by Impavidus on 2013-02-20
Most likely Windows switched to using dynamic partitions instead of primary partitions. Windows 7 always does so when you want more than four partitions. Ubuntu can't work with dynamic partitions and there's no easy way to undo this conversion. The best option is to reinstall windows on three partitions and leave enough unallocated space for Ubuntu. The Ubuntu installer can make an extended partition with multiple logical partitions inside for Ubuntu.

---

### Post by Mark Phelps on 2013-02-20
We need to see what you have ...

So, either go into Win7 Disk Management and look at the partitions there, and see if they are called "basic".  I suspect they are not, which means you will have Dynamic Disks -- which Ubuntu can't use.

Or, boot into an Ubuntu Live CD, choose Try Ubuntu, open a terminal and enter "sudo fdisk -lu" (Lowercase L, not a one), and look at the partitions.  IF they say "SFS", that is the same problem of Dynamic Disks.

---

### Post by avsksan on 2013-02-21
thank you,
         I am gonna try that.

---

### Post by avsksan on 2013-02-21
YES the windows disk management says it is dynamic disk. now what can i do. Please suggest  me with a idea.

---

### Post by Impavidus on 2013-02-21
There is no easy way to change dynamic partitions back into ordinary partitions. I think there is a way, provided you first convert to three dynamic partitions, but I don't know how it works exactly. But you wrote you installed win7 yourself, so you have an installation disk for that system. The easiest way is probably reinstalling win7, using at most three partitions and leaving enough contiguous unallocated space to add Ubuntu afterwards. This will wipe your entire hard drive. Then, don't use windows tools to make partitions for ubuntu, but use the ubuntu live disk.

---

### Post by oldfred on 2013-02-21
Best to have full backups and no more than the 4 primary partitions when you attempt to convert.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

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
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

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

---

