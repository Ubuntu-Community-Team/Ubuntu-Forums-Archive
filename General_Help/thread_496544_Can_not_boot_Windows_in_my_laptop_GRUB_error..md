---
title: "Can not boot Windows in my laptop? GRUB error."
date: 2007-07-09
forum: General Help
---

### Post by joe.turion64x2 on 2007-07-09
Hello everybody.

Yesterday I experienced a very weird problem, during the installation of my new MP3's drivers Windows XP hung and I hard rebooted (I had no choice). Afterwards I was unable to boot it again: it would not pass from the loading logo and upon displaying a BSOD rebooted itself. The BSOD appeared for a second only (or less), not enough time to read it, but after capturing the process with my camera, and analyzing the resulting video found it was an error message related to NTFS: the partition was somewhat corrupt. To mount it in Linux it was necessary to use the force option, with which I could backup all the files.

Then I got an idea: if the filesystem is screwed, lets create a new one and copy back the files. So I deleted the partition with Gparted, created another NTFS one (same size) and copied back ALL the files I had already backed up (of course I backed up the entire content). Then I expected that the next time I tried to boot Windows it would do it, however I was wrong because after selecting the proper option in GRUB it displays an error message "Unknown filesystem". It is worth noticing that the error message is not from Windows itself (at least I don't see any resemblance) and since it also shows some of the parameters in my menu.lst file I presume it is GRUB.

What could have run wrong? Is there a further step I still have to accomplish to get away with my cheat.

It is a new NTFS partition (in fact Linux mounts it flawlessly), same size, all the files are back there. The only detail there is that the label has changed (it was "ACER" and now it is empty, I did not figure out how to change it again). GRUB was not even touched.

Replacing root(hd0,0) with rootnoverify(hd0,0) solved part of the problem: the error message is no longer displayed, but the darn thing won't boot still.

Thanks.
Joe.

---

### Post by smoker on 2007-07-09
i don't think this will work, unless you had made an image copy of the partition, the reason being you're just copying files to a new partition with a different MFT than the original one that marked the layout of the files, per sector, in the drive.

saying that, though, try restoring the ntfs partition to an unallocated/unformatted partition of the same size with gparted, gparted may restore the file system as will as the data! maybe it will work that way, though i've never tried this before!

best of luck

---

### Post by joe.turion64x2 on 2007-07-09
Well, I have succeeded in my effort! I reinstalled in another hard drive, copied the whole partition using Gparted to my former hard drive, set the proper flags for the FAT32 partition (LBA, BOOT) and now I am configuring my brand new Windows XP (hell, I never thought I was gonna be so happy of watching its bloody loading logo).

And the best part is that neither my Linux partitions nor GRUB were even touched.

Thanks.
Joe.

---

