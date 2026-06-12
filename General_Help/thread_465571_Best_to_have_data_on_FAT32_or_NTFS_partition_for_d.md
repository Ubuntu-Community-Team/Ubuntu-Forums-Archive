---
title: "Best to have data on FAT32 or NTFS partition for dual boot system"
date: 2007-06-05
forum: General Help
---

### Post by bren on 2007-06-05
Does the additional NTFS tool (which I have downloaded) slow things down?
Does it work well in Feisty?

Bren

---

### Post by merlinus on 2007-06-05
I assume you mean ntfs-3g?

I have all my data on ext3 partitions.  It works very well for me, and is a more secure format than ntfs.  The journaling system allows for easier restoring, if necessary.

You can also write to ext3 from windows with the driver from

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by strabes on 2007-06-06
I second what merlinus said. When I had a dual boot I had 4 partitions: Windows ntfs, Linux ext3, Data ext3, Swap.

---

### Post by bren on 2007-06-06
hi merlinus 

yes i did mean ntfs-3g

thanks guys will try what you suggest - EDIT done it works great

bren

---

