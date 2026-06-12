---
title: "Gparted takes forever"
date: 2008-03-27
forum: General Help
---

### Post by crazlunatic on 2008-03-27
Hi. I'm trying to use Gparted Live CD to resize and move partitions. It takes 6 hours just to move and resize a 65GB partition? Why does it take so long. They are NTFS and my drives are SATA

---

### Post by cconroy on 2008-03-27
took an eternity for me as well when trying to resize partitions. i'm by no means an expert, but my guess is that it is normal.i wish there were a really fast way, but my guess is that the way the filesystems are laid out, it has to take forever if you want to preserve the existing data (as it has to rewrite each FS node to correlate to the new partition)

---

### Post by cdenley on 2008-03-27
That does seem kind of long, but it can take an hour to move that much data depending on your hardware. I think it has to resize the partition, then move it, so the files get re-written more than once. Also, gparted always does filesystem checks before and after each step since resizing/moving can sometimes create problems.

---

### Post by notwen on 2008-03-27
Resizing and moving are both very long processes.  I have done this and had a 8ish hr wait.  Hopefully you backed up whatever was on said partition, my 8 hr wait ended w/ me finding a corrupt partition.  =\
Unless you absolutely have no other option I would always recommend backing up and re-making your partitions over resizing/moving them.  Best of luck.  =]

---

### Post by forrestcupp on 2008-03-27
It all depends on what you are doing.  If you are just using empty space on the right side of your partition to make a new partition, it takes seconds.  But if you have to *move* data from one place to another to make room for a new partition, it takes a very long time.  It has to physically copy your data byte by byte from one place on your hard drive to another to free up that space.  Then the actual creating of the new partition doesn't take that long.

It would take the same amount of time no matter which partitioner you use.

---

