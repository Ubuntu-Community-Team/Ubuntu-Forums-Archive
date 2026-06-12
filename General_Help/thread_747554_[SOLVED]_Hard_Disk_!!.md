---
title: "[SOLVED] Hard Disk !!"
date: 2008-04-06
forum: General Help
---

### Post by talib on 2008-04-06
Hello every one..

I want to install Ubuntu as a second OS in my Acer Aspire 5315, but after booting via livecd it gives me only one option ( use the entire disk), while there are 2 NTFS P created, in one of those are Vista installed, 


I am having no difficulties while installing the Daulbooting in my deskop in 2 hdd , but in this case I have only one hdd..

thanx guys !

---

### Post by someonestolemyname on 2008-04-07
Are you using both of the NTFS partitions?

The reason for this is that the automatic partitioning only works for single partition.

You need to use manual partitioning, which should be available. It seems a bit complicated, but it isn't if you've ever used a partitioning utility. Just be sure to make the root (/) partition bootable and fs type ext3, make a swap partition fs type swap. 

If the second NTFS partition is for Ubuntu, reformat it as ext3 and make it '/' and bootable.

Hope this helps!

Daniel

---

### Post by talib on 2008-04-07
I have solved the problem, thank you anyway :P cheers:KS

---

