---
title: "Dual boot ! - FAT32 or NFTS for XP?"
date: 2006-07-10
forum: General Help
---

### Post by milagre23 on 2006-07-10
If we have a common partition, in FAT 32, accessible, readable and writable, both for UBUNTU and  xp is it recommendable to have the W xp in FAT 32? I didn't quite understand what are the advantages and disadvantages of NFTS or FAT 32 for the Windows partition (regarding neighbourhood with UBUNTU)!

Thanks for your attention

---

### Post by Omnios on 2006-07-10
I have a wierd set up that dates back to my original needs with a ntfs partition for linux wich used to be 50gigs and I shrunk that down to about 30 gigs wich will more than meat my windows needs, matter of fact I might try shrinking it to about 20. Anyways O have a seperate 40gig hard drive that Ubuntu is intalled on and a main 120gig that used to have 50gig win Xp and about 50 gig fat 32. Anyways this works out realy good because I use my Vfat 32 partions as my documents forlder for both XP and linux. I also read that you can get a program that will allow windows to access ext 3 but Im not shure if windows can write to it properly. Anyways I find the document partition very handy and wth Vfat it even sort of fakes permitions in Linux

---

### Post by der_joachim on 2006-07-10
Write access for NTFS in Linux is still experimental. It works, but it takes some effort to get going and it is still a bit dangerous.
If you want to be able to share files between Windows and Linux, you should use FAT32. However, NTFS is more secure and works better with large files. 

I have a small boot partition for XP, which I have formatted in NTFS, while the shared data is on a FAT32 partition.

---

### Post by MarinaraOfDeath on 2006-07-10
You want FAT32. It's the only format *easily** and *reliably* accessable in multiple operating systems. Which sucks because NTFS makes better use of space, while other file systems add in the data-saving benefits of journaling. Such is the life when using a niche OS, no matter how much it rocks.

*I've tried the native NTFS support. It reads NTFS great, but it will blow up on you after only a handful of writes. You could give the Captive NTFS system a try, some people have reported it working just fine, once they got it working.

---

### Post by helpdeskdan on 2006-07-10
Fat32, no doubt.  

Captive-ntfs has been dead for years; it is hard to get working and, last I tried, I was unable to properly delete files.

---

### Post by RAOF on 2006-07-10
You can actually use a modern filesystem on your shared drive - format it EXT3 (in Ubuntu) and you can then use the Windows EXT2(/3) driver from [www.fs-driver.org](www.fs-driver.org).  Linux NTFS write support is also getting much better - the NTFS-FUSE userspace driver is pretty good at writing (and **very** good at not killing your data - there have been no reports of corruption that I've heard of).

---

