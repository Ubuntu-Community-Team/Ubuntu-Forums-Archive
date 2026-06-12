---
title: "Rewrite FAT table on a flash drive"
date: 2008-02-15
forum: General Help
---

### Post by rado_london on 2008-02-15
Hi people,

I have a flash drive that I can't mount. I says that there is no FAT table. I used some Windows tool to view the files and the files are there, it seams that the FAT table is corrupted and I cant fix it up. How can I write new FAT table and see the files on the flash drive?

Best Regards
Radoslav Petsov

---

### Post by hardyn on 2008-02-15
Unless somebody has a better idea, format the flash disk.

man 'mkfs' for more info.  you will have to force fat32 as an agument,  and you probably want it.  

and yes, you will lose your data.  Use your windows tool to get your stuff off first, if you cannot mount the disk from linux.

---

### Post by rado_london on 2008-02-16
> **hardyn said:**
> Unless somebody has a better idea, format the flash disk.

man 'mkfs' for more info.  you will have to force fat32 as an agument,  and you probably want it.  

and yes, you will lose your data.  Use your windows tool to get your stuff off first, if you cannot mount the disk from linux.

That is the problem. The windows tool preview the data but crashes when it comes to copying. And linux says invalid file system :(:(:(

---

### Post by hardyn on 2008-02-16
can you borrow a windows box?

flash disks do not last forever, they fail just the same as a hard disk... it might just be at the end of its life.

---

### Post by vanadium on 2008-02-16
I suggest to try checking and repairing the file system with fsck. fsck normally auto-detects the file system, but if things are bad, you might want to specify the file system with the -t option: vfat for FAT32, msdos for a 16 bit FAT file system. On a Windows system, either the graphical tools or chkdsk can be used for that purpose.

A file system on a flash drive can become corrupted if it is not properly disconnected. A hardware failure indeed is also possible, although not likely in my opinion.

---

