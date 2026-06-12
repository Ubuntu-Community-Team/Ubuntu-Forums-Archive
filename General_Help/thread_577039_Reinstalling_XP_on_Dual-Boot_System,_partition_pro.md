---
title: "Reinstalling XP on Dual-Boot System, partition problems"
date: 2007-10-15
forum: General Help
---

### Post by quadomatic on 2007-10-15
I have had a XP and Ubuntu dual boot system going for some time. I resized the NTFS partition and my ext3 partition a little while back so I could get some extra space on my ext3, and now my XP installation is unbootable. But, now I want to reformat my XP partition, so I can start from scratch and try Unreal Tournament III.

Anyways, I opened up GParted Live CD, and formatted my NTFS partition, to NTFS. The partition table looks something like this (on my 160GB hard drive):

88GB - NTFS Partition
58GB - EXT3
1.5GB - Swap

When I load up the Windows XP Installer, and go to the partitioning part of the installation, the installer only shows one partition, which is labeled "Partition 1 (unknown)" which is sized at about 130,000 MB, which I think would be around 120GB. This is odd, as the NTFS partition I made is 88GB.

I didn't continue in the installer, as I didn't want to lose my linux installation.

I really don't want to tell the installer to just format over the entire thing and install, as I really don't want to lose my Ubuntu partition and all the files on it, so what can I do?

---

### Post by quadomatic on 2007-10-15
can anyone help???

---

### Post by selman_akinci on 2007-10-15
I think that is because xp cant see ext3 file formats,....... and now xp thinks you have only 1 partitioned space since it cannot see ext3.  the best way is to try your chance, but i am pretty sure if it is going to still think it is only 1 partition it will format it before installiation.... i see noway out unless you teach your xp cd to realize ext3...

---

### Post by quadomatic on 2007-10-16
The thing is, I don't think anyone else has this problem when installing XP after Linux. Usually the only problem they have is putting grub back. So, there has to be some way around this...

---

### Post by quadomatic on 2007-10-16
Any Ideas?

---

### Post by r-mo on 2007-10-16
Instead of creating the partition with gparted, delete it, so you have

88GB - Free Space
58GB - EXT3
1.5GB - Swap

Then windows installer should let you create its partition in the Unpartitioned Space

---

### Post by quadomatic on 2007-10-16
> **r-mo said:**
> Instead of creating the partition with gparted, delete it, so you have

88GB - Free Space
58GB - EXT3
1.5GB - Swap

Then windows installer should let you create its partition in the Unpartitioned Space

Thanks, that sounds like a really good idea!

It should be able to differentiate between partitioned and unpartitioned space. I'll just have to check on how to put GRUB back after I install windows.

---

### Post by quadomatic on 2007-10-17
DARNIT!!!

It still doesn't work! It can't differentiate from the unpartitioned space and then linux partitions!!!

Does anyone have any ideas?

Is it possible that this has something to do with GRUB?

---

