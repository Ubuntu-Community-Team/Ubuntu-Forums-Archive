---
title: "repartitioning/formatting old partitions"
date: 2006-11-04
forum: General Help
---

### Post by ntbutler on 2006-11-04
Heya, i am still a bit of a newbie, so i am a bit stuck...

I have 1 x 80GB HD, with 2 partitions, one NTFS which was my windows partition, one EXT2, my ubuntu partition.

In usual windows fashion, the freaking thing wont boot anymore in windows, so i want to wipe that part of the partition and make it esable for ubuntu.

Here is what i hawe done:
1. i opened up the disk manager, selected hda1 (the NTFS partition) and hit format.
2. I selected 'Extention 2' as the format type
3. I have placed the access path as '/home' and hit 'Format'. (i have also tried it on my desktop, but that had the same problem)
4. Now, in the Disk Manager Partition Properties tab, it says the filesystem is 'Extended 2' with the access path at /home, but in the size field it says 'free space not available' and in the status field it says 'Inaccessable'
5. I have pressed the 'Enable' button, many many times, but each time i press it nothing happens.

Anyone got any ideas?
Thanks.

---

### Post by jallain on 2006-11-04
After reading your post I'm left wondering if you mounted your new partition. You need to mount your partition to use it. Don't forget to put an entry in fstab so it will be done during bootup.

---

### Post by sefs on 2006-11-04
Sounds like a job for a Live CD (Knoppix & Qparted/GParted, something like that).

And i can think of two options
1) When you get into qparted and you see two partitions and you know which one is the one you wanna get ride of, you can format it as FAT 32.  Then set it up in fstab to mount to a folder in your ubuntu installation.

2) If you just want one big partition qparted/gparted I believe allows you to get rid of the extra windows partition and then grow your ubuntu partition to fill the whole space)

---

### Post by ntbutler on 2006-11-05
alright...
i have used gparted to format the partition to EXT2, but now i am having trouble mounting it.

In the fstab i have put:
> /dev/hda4       /media/hda4	ext2    defaults	0       0
(hda4 is the partition i want to mount...)

When i try to browse to the partition after running > sudo mount -a, i get into an unwritable folder with 1 subfolder 'lost+found' (also unaccessable.)

Am i doing the mount right, or did i screw up the fstab or formatting?

---

