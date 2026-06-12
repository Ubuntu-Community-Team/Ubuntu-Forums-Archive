---
title: "What is the best strategy to make complete backup of a large partition"
date: 2015-02-28
forum: General Help
---

### Post by Chromatin on 2015-02-28
Hi,
I recently set up a computer with ubuntu 14.04, using a 2Tb hard drive, which is currently divided into 243MB boot partition and a 1.8TB extended partition with LVM2.  I have tweaked the system to my liking, installing various software and storing a limited amount of data thus far.  This partition is has approx 15 GB of data.  I would now like to make a complete backup of my computer.  I am used to using Acronis software with windows, allowing me to make file-based "images" so that in case of disaster, I can restore the system to some prior state, and this works well.  It also works quite quickly, as it only backs up data, not empty disk space.  I have downloaded and read about 2 free imaging software packages, Clonezilla and Redo Backup.  As far as I understand, these are sector by sector backup packages, so would try to back up the entire 1.8 TB partition, which would take a long time and require a large disk for the backup.  Acronis also can make backups of linux partitions using its boot disk, but once again, looks like it is sector based.  I have two questions regarding options I am currently considering.  1) Are any of these packages or other software packages capable of "file based" linux backups or circumventing the large amount of empty space that I don't want to back up.  2) Should I reduce the size of the 2nd data partition (1.8TB) to something more managable (say 50 GB), therefore making the sector by sector backups quicker.  Further, I have looked at gparted to do the second item, and was wondering if there is a risk to reduce the partition size from 1.8 TB to 50 GB.  I assume the software would let me know if I reduce the partition size too much, and loose data, correct?

---

### Post by TheFu on 2015-02-28
1) clonezilla will compress the resulting image.  Most tools will - partimage, fsarchive are other F/LOSS options. File based backups are a different thing, entirely.

2) Post the output from **sudo fdisk -l** - please use "code tags" so things line up. Also, long paragraphs are hard to read. Please use line breaks.  A table with partition devices, sizes and mount points would be helpful.  **df -h** please.

3) Linux does what you tell it to do. Sometimes it doesn't warn you, since you are smarter than the computer and told it what to do.  If you do dangerous partition things and don't want to lose data, YOU need to make a know-you-can-restore backup.

LVM complicates bit-for-bit backups.  It really comes down to the level you decide to back up - you pick by choosing the whole drive device, partition device or a specific file system inside.  If you pick the wrong device, you'll not have the backup you want.  OTOH, this flexibility means you can get exactly what you want, when you want it.

Personally, I don't see the need to do image-based backups on Linux systems and don't actually backup anything that can easily be restored by reinstalling a fresh OS from an ISO, then restoring OS settings, my data and installing the same applications that were there before the failure.  Takes about 30-45 min to restore most of the servers here, but the restore isn't brain dead.  Having a brain-dead restore does make sense in many situations - it also wastes 4-10G per OS install and limits the number of versioned backups I can retain.  Normally 60 days is possible and for some high-risk systems, we keep 120 days of versioned backups. Can't do that with images - even if compressed.

Oh ... see how much easier it is to read with the line breaks? ;)

---

### Post by gakon77 on 2015-02-28
Hi, first to say I'm no expert.
However, from my experience with Clonezilla and after some research prompt by your question, I can tell you that the size of the image resulting from the partition will be even smaller than the volume of data that the partition in question contains[*]("http://drbl.org/faq/fine-print.php?path=./2_System/56_space_required_for_clonezilla_image.faq#56_space_required_for_clonezilla_image.faq"). I seems that Clonezilla not only ignores the empty space, but also compresses the data by default.

Also, you need to know that Clonezilla will restore your image to a partition which is the same size as the original partition. So if you cloned a 1.8Tb partition, the recipient for the restored image must be 1.8Tb.

Now, to the question of resizing partitions. 
Gparted will resize your partition and personally never had a problem with losing data. However, it's worldwide-strongly recommended to backup essential data before.

Can't say anything about Acronis.

Cheers!

* - [http://drbl.org/faq/fine-print.php?path=./2_System/56_space_required_for_clonezilla_image.faq#56_space_required_for_clonezilla_image.faq](http://drbl.org/faq/fine-print.php?path=./2_System/56_space_required_for_clonezilla_image.faq#56_space_required_for_clonezilla_image.faq)

---

### Post by Chromatin on 2015-02-28
Hi,
Thanks for the advice from the two people that responded to my post; the comments were quite useful.  After reading the posts, maybe I'll try out Clonzilla and see how long it takes and how large a backup it generates.  

I'll try and remember to reorganize my posts to make them more readable as well.

---

### Post by Bucky Ball on 2015-02-28
With Clonezilla, the backup needs to be to a partition _the same size_ as the one you're backing up. For instance, if you have a 500Gb partition with only 30Gb used, makes no difference. It must be cloned to a 500Gb partition or larger. 

When restoring, as mentioned, it must be to a partition the same size as the one you're restoring from or larger. 

To shrink the partition prior to cloning, boot Live media>Try Ubuntu>Gparted>Unmount the drive you want to shrink (right click)>shrink.

As mentioned, ALWAYS backup anything you don't want to lose. Here's some help with Clonezilla:

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Good luck.

---

### Post by TheFu on 2015-03-01
fsarchive can restore to a smaller partition, provided the data will still fit.

Many of these tools don't work as smart for ext4 or btrfs partitions as they do on ext3. Read the fine print.

---

### Post by Bucky Ball on 2015-03-01
Clonezilla's always been fine for me, but only used it on NTFS and EXT4 partitions. From their [site]("http://clonezilla.org/"):

> Many File systems are supported: (1) ext2, ext3, **ext4**, reiserfs, reiser4, xfs, jfs, **btrfs** of GNU/Linux, (2) FAT12, FAT16, FAT32, NTFS of MS Windows, (3) HFS+ of Mac OS, (4) UFS of FreeBSD, NetBSD, and OpenBSD, (5) minix of Minix, and (6) VMFS3 and VMFS5 of VMWare ESX. Therefore you can clone GNU/Linux, MS windows, Intel-based Mac OS, FreeBSD, NetBSD, OpenBSD, Minix, VMWare ESX and Chrome OS/Chromium OS, no matter it's 32-bit (x86) or 64-bit (x86-64) OS. For these file systems, only used blocks in partition are saved and restored. For unsupported file system, sector-to-sector copy is done by dd in Clonezilla. 

:)

---

