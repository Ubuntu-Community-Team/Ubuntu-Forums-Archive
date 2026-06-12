---
title: "I defraged a FAT partition and now nautilus is..."
date: 2007-07-18
forum: General Help
---

### Post by SteveRHCI on 2007-07-18
I use a FAT32 partition to hold data files used on a dual boot laptop using Windows XP and Feisty Fawn.  When running under XP I defragmented the FAT32 partition.  Now nautilus is showing more than 11,000 files in the Found folder and the found files are far too large to just be bits of files.

How do I recover from this?  I fear that if I delete a file in the found folder it may damage a good file.

Will booting in XP, backing up the data on that partion, formating the partition and restoring the data to the partition clear the found folder?

Any suggestions will be greatly appreciated.

---

### Post by Sef on 2007-07-18
Have you checked out [TRK]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12")?

---

### Post by undecidable on 2007-07-18
1.  I assume that Wz sees the Fat32 as OK and with no problems.  
If this is not the case, ignore the below.

2.  If so, the problem might be just with Lx's view of the partition,
not with the partition itself,
in which case I agree I would be very careful before messing with it.
I don't know, but it appears Lx is storing a "view" of the filesystem structures between reboots
and when the files are changed not by Lx, it suffers a mismatch between
what it thought should be there and what is there. 

3.  My first inclination if it happened to me
(assuming 1. and 2. above)
would be to try to get Lx to re-initialize it's view of the filesystem.
a.  unmount and remount the fat32 partition.
or if that is not sufficient:
b.  umount, remove the fat32 partn from the fstab,
reboot, mount the partition manually and then check it.

If the errors are still there then - well I am at a loss.

---

### Post by SteveRHCI on 2007-07-18
Thanks to both of you for responding.  TRK looks interesting and I learned a lot about fstab by reading various how-to articles (I am relatively new to linux and have much to learn yet).

It turns out that Windows also had problems with the partition and found many corrupted files that it appears to have fixed.  I will be poking around in that partition for a while to see if everything is good but at this point it appears to be fixed.

Thanks again.

---

### Post by HermanAB on 2007-07-18
Hmm, the moral of the story is: Don't use FAT, especially on removable drives.  It is not robust enough for use on anything bigger than a 128KB single sided floppy disk...

If you require the data to be readable by both Windoze and Linux, format with NTFS and use ntfs-3g on Linux to access it.

Cheers,

Herman

---

### Post by merlinus on 2007-07-18
Another option is to format as ext3 and use the ifs drivers to write from windows.

Both work great, for me.

-merlin

---

