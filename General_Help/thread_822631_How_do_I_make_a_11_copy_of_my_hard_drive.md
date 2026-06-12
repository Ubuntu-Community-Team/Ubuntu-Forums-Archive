---
title: "How do I make a 1:1 copy of my hard drive?"
date: 2008-06-08
forum: General Help
---

### Post by edbyford on 2008-06-08
Hello all

I am looking for a program that will make a 1:1 copy of my hard drive. I know that you can relatively easily copy a partition, but I'm talking about the whole hard drive.

I just bought a new hard drive (500gb) to replace my current 500gb, which seems to be failing. I don't want to have to bother to recreate all the partitions etc (as I am dual-booting XP and Ubuntu 8.04) so I just need a program which will help me do this. 

I don't want/need compression, and would like it to be able to omit free space from the copy, although this is not essential.

Thanks in advance

---

### Post by ScottLij on 2008-06-08
I recently used this software which will put the hard drive image on a FTP server:  [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/) .  I tested it out and it worked great and had about 50% compression.

---

### Post by edbyford on 2008-06-08
I don't have an FTP server. Can this clone to a local drive?

---

### Post by .nedberg on 2008-06-08
g4u as mentioned above or
[g4l]("http://sourceforge.net/projects/g4l")
[partImage]("http://www.partimage.org/Main_Page")

Never tried any of them, but I have heard partImage is a great program. I am going to use it this July when I am upgrading my Dapper server to Hardy.

---

### Post by edbyford on 2008-06-08
I need it to be able to make a 1:1 copy of the drive, with partition sizes and positions intact. I think that partimage only copies individual partitions. Can anyone confirm this?

---

### Post by sisco311 on 2008-06-08
You can use **dd **command to copy the whole disk.
dd copies everything including blank space (byte for byte).
The syntax:
```
dd if=/dev/sd**X** of=/dev/sd**Y**
```if = read from file (old disk)
of = write to file (new disk)

EDIT: This command is **dangerous**. If you do it wrong you can **lose all your data**.

---

### Post by edbyford on 2008-06-08
dd copies everything, even the partition information? so it would be indistinguishable from the original disk?

---

### Post by bingoUV on 2008-06-08
> **edbyford said:**
> dd copies everything, even the partition information? so it would be indistinguishable from the original disk?

yes. If new disk is larger, there will be free space at the end

---

### Post by sisco311 on 2008-06-08
> **edbyford said:**
> dd copies everything, even the partition information? so it would be indistinguishable from the original disk?
Yes, but this command is [SIZE=4]**very dangerous**[/SIZE].
**Be real careful.** 

First post the output from:
```
sudo fdisk -l
df
```and the command you want to execute.

---

### Post by ScottLij on 2008-06-08
> **bingoUV said:**
> yes. If new disk is larger, there will be free space at the end

You can then use GParted to "reclaim" that free space by resizing the partition.

---

