---
title: "mount.ntfs process bogs my system to a crawl."
date: 2016-05-15
forum: General Help
---

### Post by pjstock on 2016-05-15
I'm using Ubunut 14.04.

on an admittedly kind of old (and maybe completely outdated) desktop
Memory 4Gb
Processor: Intel® Pentium(R) Dual CPU E2200 @ 2.20GHz × 2 
OS Type 32 bit
Disk 20gb (thatt's for the Ubuntu partition, with about 4Gb free)

Lately I notice that at a certain point the system slows to a crawl. (a 4 second delay between hitting a key and the character showing on the screen.)

a little time with System Monitor and it appears that the slowdown occurs when I Mount a certain internal HDD (250gb).
(I added this drive as just a spare, somewhere I could drop files or store backups.)

at that point the mount.ntfs process shows up and CPU usages surges to 100%.
(Interestingly too, this HDD doesn't auto-mount when I boot the system. I have to manually mount the drive on each reboot.)
So, clearly there is something wrong with the way this HDD is installed.
I am cleaning it off so that I can reformat it.
Any suggestions on how I should do that? what type of format should it be for Ubuntu?

Peter

---

### Post by Mark Phelps on 2016-05-15
Curious as to why you're mounting an NTFS volume -- as you would only need to do that if that volume was shared with a Windows installation.

My guess is that the NTFS volume needs chkdsk run on it -- and you can only do that from Windows.

---

### Post by pjstock on 2016-05-16
In the end, I cleaned off this HDD, and just reformatted it.
First as FAT (because I thought NTFS was causing the problems) but then, once i realized how limiting FAT filesystem was, again as NTFS.
This seems to have cleared things up.
I am not having the same slow down problems.
So I expect that there was a problem with the disk itself that the reformat fixed.

---

### Post by Mark Phelps on 2016-05-16
Understand this is fized, but unless you really need this formatted NTFS for Windows, my suggestion would be to reformat it FAT32.  

The main problem with NTFS is that there are no Linux tools for fixing serious filesystem problems.  

So, unless you can boot into Windows and run CHKDSK on that partition, if the filesystem gets corrupted, you're stuck with an unusable filesystem.

Good Luck

---

### Post by pjstock on 2016-05-16
sigh.... thank you.
but I thought that FAT 32 was limited to a 32Gb partition and files no bigger than 4gb or something along those lines.
is that not true?
when I tried to transfer some files back onto the disk in FAT32 format, it failed, I believe on some files being to big.

---

