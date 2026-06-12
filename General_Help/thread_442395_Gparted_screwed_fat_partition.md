---
title: "Gparted screwed fat partition"
date: 2007-05-13
forum: General Help
---

### Post by spupy on 2007-05-13
Today i noticed that my Ubuntu partition has about 7GB unused space. So i decided to move that free space to my general storage fat32 partition. The problem was that all partitions were something like this:
- NTFS
- Ubuntu
- Extended:
       ---- Swap
       ---- Gentoo Partition
       ---- FAT32 partition

So first it had to move the 7GB from the ubuntu partition to extended and then jump over the swap and gentoo, add the space to the fat32, and (im not sure if this is required), move the entire fat32 7gb to the left.
Ok, so i fired up my Linux Rescue CD, gave Gparted the commands and left the PC for 30-45 minutes, since i knew that moving a big partition requires a lot of time...
But when i got back,  Gparted was not running. After i ran it again, everything was "ok", except that these 7GB were at the end of the HD, where they were supposed to be, but they were still unallocated. AND what is the main problem, the moved fat32 is not recognized as a fat32. It cannot be mounted by linux or windows.

I tried several utilities for partition info and restoration, the all said stuff like: unknown, unformatted, corrupted filetable. Some find out that it is fat32 but still unformatted. Whats bothering me is the one that says "unformatted". 
I dont know if the information is still on the partition, or even if it was correctly moved. I cant yet access it. Is there any way to recover the files from that partition, or even better, just "fix" it?
This is a screenshot from gparted
(And im sorry for the long post, i just wanted to explain everything because i really need to recover my data, nothing of great value but still...)
Thanx for every responce!

---

### Post by spupy on 2007-05-13
Nevermind! Fixed it with TestDisk! Beautifull program. Thanks to ubuntuforums! Woohoo!

---

