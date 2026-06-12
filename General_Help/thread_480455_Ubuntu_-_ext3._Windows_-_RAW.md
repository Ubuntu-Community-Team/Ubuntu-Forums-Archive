---
title: "Ubuntu - ext3. Windows - RAW?"
date: 2007-06-21
forum: General Help
---

### Post by Xe_Sn@kE on 2007-06-21
Hellu

I need a little help with my hardisk/partition problem.
ok the story is:
I'm running Ubunto for some weeks anfd works perfect, then i deside to install Win XP for dual boot,
 so i do.
I formated my "OS-disk" and installed Win XP on one partition and reinstalled Ubuntu on same disk (ca 50gb each).
but then, i allready have two 250gb disks (both ext3) (+ my "OS-disk" with ntfs, ext3 and swap), all the disk is working fine in ubuntu, i can read and write to all of them (exept swap :p) BUT in the bios it tells me that one of my 250gb disk is only 34 gb or so, and windows think so to (natuarly) exept for Norton partition magic (surprise!) and tells me that it's a RAW/FAT-16/32 disk.

so now for my question:
how to fix this problem without formating the hd? (it worked fine earlyer (the bios didn't say it had only 32gb either, only after installing win XP))

thanks

---

### Post by LaRoza on 2007-06-21
What does Ubuntu say about the partition sizes?

If you want a good partition and formating tool, use GParted Live Cd, check my sig, it works with many partitions formats, including all the Linux ones, the FAT's, and Swap, among others.

BIOS will report a large disk as smaller if it is an older BIOS. As long as you can use the entire disk, no problem exists. 

Windows will not work with ext3, if you want a disk for sharing, use FAT32.

---

### Post by Xe_Sn@kE on 2007-06-21
Ubuntu say both my 250gb it's around 236gb (i used Gnome partition :p)

and the bios got the right size on the other disk that is exactly the same size so why not that one? :p

and ext3 disks works fine as long as i got the ext2 driver installed so that's no problem ;)

---

