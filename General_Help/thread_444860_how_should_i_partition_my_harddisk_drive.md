---
title: "how should i partition my harddisk drive"
date: 2007-05-15
forum: General Help
---

### Post by atlfalcons866 on 2007-05-15
hi 
i installed windows xp on my new 160Gb harddisk. I didnt mean for windows to take up all the space. how many gigabytes should i give ubuntu? is 40 GIGs enough? should i create a root and home partiton.? i dont want to reinstall windows because i dont want to go thourgh the updates again. will ubuntu run faster if it is in the last 40GBS of my harddrive?

---

### Post by NilsE on 2007-05-15
40 gigs should be plenty unless you have a lot of music etc.  I run Ubuntu on 20Gig  hard drive partition and the remainder is shared between Ubuntu and XP

You should be able to use the Gnome partition editor to shrink the XP partition and create the others.  One partition ext3 for Ubuntu and one for swap should be sufficient.

---

### Post by loserboy on 2007-05-15
Ubuntu and programs you install in it uses roughly the same amount of space, so it really depends on how much stuff you plan on installing, 40 gigs should be fine, you could always change it later if you want.

you have to create a / (root) partition and a swap partition, the swap should be around double the amount of ram you have but no more than 1 gig i think they say. it's your choice if you want to make a /home partition, alot of people do, I usually don't.  a /home is kind of like a documents and settings folder.

---

### Post by rich.bradshaw on 2007-05-15
/home on a seperate partition is an awesome idea. If you reinstall you don't lose any documents.

---

### Post by pixellany on 2007-05-15
If you just installed Windows, it will not be difficult to resize the partition--using something like GParted.
I would have mabye 15GB for Windows, 10GB for Linux, and the rest for one or more data partitions.
AND....leave empty space on the disk for future additions.

As far as i know, the location of a partition does not affect speed.

---

### Post by juamez. on 2007-11-06
The location of the partition actually does affect speed. The first partition is the fastest because it is situated towards the outer edge of the platter(s), which has the highest data throughput at a given rotational speed. The same reason why CD/DVD-Writers increase (or decrease?) speed while progressing in the burn-operation. A CD/DVD starts at the innermost part of the disk, whereas a hard disk starts at the outer edge, thus delivering best performance for the first half (a rough estimate) of the disk's capacity. This can be backed up with HDTach performance graphs.

---

### Post by atlfalcons866 on 2007-11-11
> **juamez. said:**
> The location of the partition actually does affect speed. The first partition is the fastest because it is situated towards the outer edge of the platter(s), which has the highest data throughput at a given rotational speed. The same reason why CD/DVD-Writers increase (or decrease?) speed while progressing in the burn-operation. A CD/DVD starts at the innermost part of the disk, whereas a hard disk starts at the outer edge, thus delivering best performance for the first half (a rough estimate) of the disk's capacity. This can be backed up with HDTach performance graphs.

dvd/cd writers and cd/dvd readers spin the disc the fastest at the beginning of the dvd/cd. Not sure of blu-ray/hd-dvd discs though

---

