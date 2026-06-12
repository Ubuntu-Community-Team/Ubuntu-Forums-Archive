---
title: "Partitioning Issues"
date: 2008-01-22
forum: General Help
---

### Post by Wan_Lin on 2008-01-22
Hi, I recently installed 7.10. I had Windows XP installed already and wanted a dual boot, so I started the whole process.

Upon reaching the partitioning step, I made the partitions, and now I have Linux and Windows, everything's great.

Except I must've not understood the partition screen, because my windows partition is small (and my linux partition is big) when I wanted the windows one to be the big one.

Is there a way to re-partition linux to a smaller one, and take the free space and put it back into my window's C drive? Windows is running slow now due to lack of space.

Thanks in advance!

---

### Post by LaRoza on 2008-01-22
> **Wan_Lin said:**
> Hi, I recently installed 7.10. I had Windows XP installed already and wanted a dual boot, so I started the whole process.

Upon reaching the partitioning step, I made the partitions, and now I have Linux and Windows, everything's great.

Except I must've not understood the partition screen, because my windows partition is small (and my linux partition is big) when I wanted the windows one to be the big one.

Is there a way to re-partition linux to a smaller one, and take the free space and put it back into my window's C drive? Windows is running slow now due to lack of space.

Thanks in advance!

When you moved the slider, you probably misinterpreted what it meant, I have seen it happen with other people, not really unique.

Yes, you can do what you want. First, get GParted Live CD (or use the Partition Editor on the Ubuntu install disk) and manually make the partitions that you want. You will have to delete the Linux partitions and make the Windows Partition larger. It is an easy GUI tool, so it isn't complicated.

Then, make the partition for Linux and the swap partition (I recommend 512 MB).

When you install Ubuntu, manually select the partitions to install to.

(Note, I assume you have everything backed up. This is usually safe, but if something happens data can be lost)

My personal preference is to make the Windows and Linux partitions small (15 GB) and make a large partition for data which I use for storage. I make the large partition NTFS so I can put the Windows page file on it, and have read and write access from Windows and Linux.

---

### Post by Wan_Lin on 2008-01-24
Can I not just create a partition in Ubuntu (with whatever tool within Ubuntu does that) with NTFS file system, go into it from windows, and delete it, putting it into the free space of windows?

If not, do you mean that I have to completely remove Ubuntu from my computer in order to fix this? Because that sucks.

Looking forward to anyone's futhered advice!

---

