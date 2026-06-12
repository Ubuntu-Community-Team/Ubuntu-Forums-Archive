---
title: "Changing partition table, creating new mountpoints"
date: 2007-06-07
forum: General Help
---

### Post by config on 2007-06-07
Hello everybody!
I have installed Feisty several months ago and it's working pretty good. But now I'm thinking about changing partition table. I have following mountpoints:
1. /dev/hdc6 / - 17Gb
2. /dev/hdc7 linux-swap - 1,5Gb
3. /dev/hdc8 /home - 6Gb

I'm thinking of resizing the first one to 10Gb and last one to at least 10Gb (downloading gparted LiveCD now), creating separate partitions for "/var" and "/usr".
So, questions are:

1. Is it possible just to create partitions with mountpoints "/var" and "/usr" and add them to fstab so Linux uses them to store all the data instead of folders in "/" or should I do something else?
2. Does it worth all the trouble? May be I shouldn't bother myself with creating those 2 partitions?
3. If it worth the trouble, is 1 Gb for "/var" and 2Gb for "/usr" enough?

---

### Post by vanadium on 2007-06-07
If this isn't a server, i would not bother creating more partitions than you already have. For personal desktop systems, I am even in favor not to create a separate home partition. Yet indeed, all Linux needs to know to mount partitions at boot time is in the fstab file, so yes, it would suffice adding in these partitions. that would answer all your questions according to my opinion.

---

### Post by config on 2007-06-08
Thank you for answering all the questions :).
Now I have next series of questions :). I can decrease size of "/" in Gparted but unfortunately, I can't increase size of "/home" - it simply doesn't allow me to move "/home".
1. Why? What can be wrong with it?
**2. Is it possible to do all these actions in, for example, Partition Magic or any other windows program without damaging Linux?**
3. Are there any other programs in Linux that allow to move and resize partitions?

---

### Post by config on 2007-06-13
bump

---

### Post by vanadium on 2007-06-13
This forum is so busy that it is easy to loose a thread out of sight when not subscribed to. Anyway, I am not a partitioning specialist, but I still can add something here. I am surprised to learn that GParted could not move a partition. I think it can, but the partitions can probably not be in use. Thus, you should run gparted from the live CD or from the dedicated gparted boot disk. Then I am pretty sure you will be able to move the partition, then enlarge it until it touches your "swap".

I have no experience with Partition Magic, but rumours are that it does not support Linux ext3 file systems well.

---

### Post by strabes on 2007-06-13
DON'T use any windows program to change ext3 (or any filesystem besides ntfs/fat32/fat16) partitions around.

---

### Post by config on 2007-06-14
Thanx for advices.
Found topic with some additional info I wanted to know: [http://ubuntuforums.org/showthread.php?t=328677]("http://ubuntuforums.org/showthread.php?t=328677")

My problem is that GParted Live CD is loading, the gparted program starts but when I move mouse, system hangs. I tried different boot options but non of them help. Looks like I'll have to find a way to resize partitions using "parted" from Live CD :(. Is it hard to do?

---

