---
title: "Having problems resizing/moving NTFS partition with GParted"
date: 2008-04-24
forum: General Help
---

### Post by capo327 on 2008-04-24
First of all, I'm using the LiveCD for the actual partitioning, but I'm using the install for the screenshots.

I realized I had too much space on my windows partition and I ran out of space on my data partition, so I tried resizing.  The problem is that whenever I try to enter a new number for the size of the data partition, it returns to the current number.  Someone I asked told me I can't place the unallocated space in the partition unless it's after the data and I'd have to move it around, but I can't move the partition either.

In case this helps:

[IMG]http://img182.imageshack.us/img182/2760/screenshotip9.jpg[/IMG]

[IMG]http://img126.imageshack.us/img126/5389/screenshot2bk0.jpg[/IMG]

---

### Post by capo327 on 2008-04-24
Any help?

---

### Post by logos34 on 2008-04-24
The unallocated space is INSIDE an extended partition.  SO you need to shrink sda1 first, THEN expand/grow sda2 to the left into the empty space.

---

