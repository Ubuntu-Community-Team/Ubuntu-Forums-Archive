---
title: "General maintenance"
date: 2008-03-22
forum: General Help
---

### Post by Hoppes on 2008-03-22
HI,
I just switched from Windows XP to Ubuntu. After exploring around I didn't find any maintenance programs like disk defragger or disk cleaner that xp had. Do you not have to do those when running ubuntu? If you do can you please tell me how, and if you dont have to, please tell me why not, 

Thanks

---

### Post by Distro Jockey on 2008-03-22
As ext3 is the most common filesystem for Linux's, this quote from wikipedia on ext3 may help explain why defragmenting is not really necessary.

> There are userspace defragmentation tools like Shake[8] and defrag [9]. Shake works by allocating space for the whole file bolt upright and hoping that it will make the newly allocated file less fragmented. It also tries to write files used at the same time next to each others. Defrag works by copying each file over itself.
However they only work if the filesystem is reasonably empty. A true defragmentation tool does not exist for ext3.[10]

That being said, as the Linux System Administrator Guide states, "Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system."[11]

See the full entry at:  [http://en.wikipedia.org/wiki/Ext3]("http://en.wikipedia.org/wiki/Ext3")

As for disk cleaning/checking this is done automatically at boot time, or you can manually use:  fsck

---

### Post by Existentialist on 2008-03-22
You will not need these utilities with linux.  If you want to know more about why the filesystem doesn't become fragmented in linux, this is one of the clearer things I have seen about it:

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by NightwishFan on 2008-03-22
Some times I boot into a Windows and run a defragger just for old times sake. :lolflag:

Yeah under most reasonable circumstances cleaning and defragging are not needed as the OS maintains itself better.

---

### Post by Hoppes on 2008-03-22
Thank you all very much!

---

