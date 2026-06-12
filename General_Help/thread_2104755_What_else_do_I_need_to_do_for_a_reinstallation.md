---
title: "What else do I need to do for a reinstallation?"
date: 2013-01-14
forum: General Help
---

### Post by Man_Beach on 2013-01-14
I had a few problems installing 12.04 and had to re-install 10.04 (needed a working computer that evening and didn't have the time to fiddle about trying to get it working properly). All I'd done in the way of backups was to copy the visible files in my home directory onto an external hard drive, which I'd planned to copy over to my new home directory - this is what I've done in previous updates.

It didn't take too long as I still had my 10.04 live CD and after downloading 200-odd updates and copying back my files things were back pretty much as they were before.

Before I try installing 12.04 again, I'd like to make a backup of my working system this time so that if things go wrong again I can restore things as they were, a little quicker.

I have a separate home partition. I understand that I can use something like Clonezilla to make a copy of my home directory (/home) to an external drive and then restore it later - do I also have to take a copy of the root file system (/)? 

What else do I need to do? I presume that I'll somehow need to put the grub2 menu back as it was as well? If so, how do I do that, please?

---

### Post by howefield on 2013-01-14
+1 to Clonezilla.

It will put grub back on for you if you clone the disk (or partitions) to image, And save you reinstalling and downloading updates, or at least as many of them.

---

### Post by mastablasta on 2013-01-14
clonezilla though powerfull has strange menues. one wrong selection and you have to redo the whole thing procedure from the start. unless ofcourse you already know what you want. then you can probably use command line as well.
 
you could try redo backup. it uses same backup technique and programmes as clonezilla, but it has a much nice user interface.

---

### Post by howefield on 2013-01-14
Clonezilla looks more intimidating than it actually is, most times walking through the "wizard" taking the default options will be perfectly good and easy but you do need to read the screens :)

I would recommend accepting the check file system and check image is restorable options though.

---

### Post by offgridguy on 2013-01-14
Just a related question, will clonezilla work for windows as well??

---

### Post by howefield on 2013-01-14
Yes it does support Windows file systems.

> Filesystem supported: (1) ext2, ext3, ext4, reiserfs, reiser4, xfs, jfs, btrfs of GNU/Linux, (2) FAT12, FAT16, FAT32, NTFS of MS Windows, (3) HFS+ of Mac OS, (4) UFS of FreeBSD, NetBSD, and OpenBSD, and (5) VMFS3 and VMFS5 of VMWare ESX. Therefore you can clone GNU/Linux, MS windows, Intel-based Mac OS, and FreeBSD, NetBSD, and OpenBSD, no matter it's 32-bit (x86) or 64-bit (x86-64) OS. For these file systems, only used blocks in partition are saved and restored. For unsupported file system, sector-to-sector copy is done by dd in Clonezilla.

---

### Post by Man_Beach on 2013-01-14
> **howefield said:**
> +1 to Clonezilla.

It will put grub back on for you if you clone the disk (or partitions) to image, And save you reinstalling and downloading updates, or at least as many of them.

Thank you howefield. That's all I needed to know. And also mastablasta - I'll have a look at redo backup.

---

### Post by offgridguy on 2013-01-14
Thank you howefield.

---

### Post by Man_Beach on 2013-01-30
As a footnote, I can confirm that Redo Backup is very simple to use. I used it to back up my root and home partitions, and after some more experiments (still haven't managed to get things working properly yet), I used it to perform a restore which fully returned everything (including Grub) exactly as it was before I started playing about. Marvelous!

---

