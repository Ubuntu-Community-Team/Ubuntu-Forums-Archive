---
title: "[SOLVED] Data sharing between Linux and Windows system"
date: 2007-11-01
forum: General Help
---

### Post by Bheegerji on 2007-11-01
I'm new to Linux. I'm planning a clean install of Ubuntu 7.10 for my system completely removing Windows XP. And, I've been reading various posts on data sharing between Windows and Linux systems. As most of my pals have Windows, I'll have to constantly share files and documents with them and vice versa. 

What happens if files on a Linux system (ext3 formatted) are copied onto a pen drive or burnt on a DVD or CD and accessed on a NTFS formatted Windows system? Will the Windows system be able to access these contents?

If it's the other way around, will my Linux system be able to access these data?

If portable storage cannot be a possible solution for data sharing between these two systems, please recommend me one.

Thanks.

---

### Post by dayvy on 2007-11-01
When you burn a disc it doesn't copy over the file system from the host computer. DVDs and CDs use their own file system which is accessible by most, if not all, operating systems. You'll have no problem with your pendrive if it's formatted with vfat. Both linux and XP will read and write to it.

d.

---

### Post by Bheegerji on 2007-11-01
Thanks man.

That clears it.

---

### Post by rubicon on 2007-11-01
> **Bheegerji said:**
> What happens if files on a Linux system (ext3 formatted) are copied onto a pen drive or burnt on a DVD or CD and accessed on a NTFS formatted Windows system? Will the Windows system be able to access these contents?It's all depends on which file system (FS) used on that media. If that is USB pen drive, then it's most certainly FAT32 (which is OK for both Windows and Linux). If that is a DVD or CD, then its FS is most certainly UDF or ISOxxxx (fixme!), which are also OK for both types of systems.

I mean, every media uses its own FS, that is - if you use Windows XP, then the disk on which it was installed is NTFS, but other disks (or partitions on this disk) may have other FS (even Ext3 and ReiserFS).

---

### Post by rubicon on 2007-11-01
[Addition]
Even if you use Ext3 FS for your pen drive, you can access it from WinXP using special drivers.
And vice-versa, Ubuntu supports NTFS (both for reading and writing).

---

### Post by mahousaru on 2007-11-01
Even though this is solved, I'd just like to point out a warning if you are using the ext2 ifs drivers.  they can't handle utf8 very well when means if you use multiple languages for your file names you can end up corrupting them.

---

