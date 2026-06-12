---
title: "How do I make the swap partition bigger?"
date: 2007-02-21
forum: General Help
---

### Post by Zeroangel on 2007-02-21
Hi all,

I recently have been getting lockups on a PC that I installed ubuntu on. And a lot of them are due to memory problems.

First off, I have 239MB of available RAM (due to integrated graphics) and a 128MB swap partition.

Is there a way that I can resize the swap partition without erasing the data partition on the same drive?

---

### Post by Xzenome on 2007-02-21
Download the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and resize an ext2, ext3 or fat32 and put it into the swap partition.

---

### Post by po0f on 2007-02-21
Zeroangel,

You could also just add a [swap file](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html) so you don't have to resize your partitions.

---

### Post by Zeroangel on 2007-02-21
Thanks a lot gentlemen! Creating a swap file was the easiest thing to do (and less risky) so I did it and it works like a charm. :KS

---

