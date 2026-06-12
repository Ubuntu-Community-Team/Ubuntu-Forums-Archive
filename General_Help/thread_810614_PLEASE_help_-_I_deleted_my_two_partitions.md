---
title: "PLEASE help - I deleted my two partitions"
date: 2008-05-28
forum: General Help
---

### Post by blazemore on 2008-05-28
I wanted to do something to my USB-flash drive, so I opened gParted from the Live CD, selected both partitions, deleted and formatted as FAT32.

Then I realised it was my Windows and Backup partitions on my 250gb main hard drive, with my OS, programs, work and media on.

Using TestDisk, or otherwise, is there any way I can get the original two back? Nothing has been writted to the new Fat32 volume, and I am still in the Live CD (I have Universe enabled)

Can Anyone Help!???

---

### Post by Zorael on 2008-05-28
Well, go ahead and try; if testdisk can't fix it, you'll likely need (expensive) professional help.

---

### Post by persistentstubborn on 2008-05-28
First, calm down.

Testdisk will do it. Go and download it (you probably already had).

**Caution**: Find partition from where you'll run testdisk, it ought to be at least as large as partition you recover. Otherwise, your session will be interrupted. The gravest mistake you can do is to start recovering from an insufficiently large partition (that's the experience, my friend).

---

### Post by blazemore on 2008-05-28
OK right.

TestDisk has found a load of partitions (some are old)
They are in a list. How do I select one for recovery?

---

### Post by blazemore on 2008-05-28
Anyway I give up now. I'm totally reinstalling Vista again (I love Ubuntu but it doesn't work with my wireless card without pointless fiddling)
I'll copy my music off my MP3 player, and my work off my server in Houston.
I'll run a Windows file recover software to get as many individual files back as I can.
Money no object *ahem* what software would you reccommend, have you had experience with this in the past?

---

### Post by persistentstubborn on 2008-05-28
Testdisk (and photorec, I think they are separate in Gnjinjdows), works under windows, too. Go to [www.cgsecurity.org](www.cgsecurity.org) and download version your system requires.

However, by reinstalling Vista prior to recovery, you seriously decrease chances to recover anything.

If I were you, I'd first get a separate HDD (perhaps purchase a new one), load it and format under Ubuntu live, download testdisk and ntfs-3g driver, cd /media/justpurchasednewdiskofenoughspace and type the command testdisk.

That'll do.

---

### Post by fsmithred on 2008-05-28
If you have a copy of the output of fdisk -l from before the catastrophe (or if you wrote down which cylinders each partition starts with), you can rebuild the partition table with sfdisk. Just keep in mind that fdisk starts counting cylinders at 1 and sfdisk starts at 0, so you'd have to adjust the numbers when you rebuild. (Note: This only works with primary partitions, not logical.)

---

