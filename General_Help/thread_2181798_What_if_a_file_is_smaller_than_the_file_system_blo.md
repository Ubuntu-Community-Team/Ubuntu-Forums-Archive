---
title: "What if a file is smaller than the file system block?"
date: 2013-10-19
forum: General Help
---

### Post by mosquetero on 2013-10-19
Hi!

I have a quick question, I am reading that ext 3 has a block size of 4 KB. What happens if I save a file that has 2 KB of size. Will the file system fill it with 2KB of zeros? Or will it wait until there is an extra 2KB to be written in order to fill the block?

Thanks!
Manuel

---

### Post by Johan De Cauwer on 2013-10-19
I don't think the OS would bother writing anything in that unused space. So it's undetermined. But that's a way to lose space, yes. However, on a disk of say, 500 GB...

---

### Post by mosquetero on 2013-10-19
Hi Johan

Is it a guess or are you sure about it?

Thanks

---

### Post by The Cog on 2013-10-19
Reading his words, Johan De Cauwer sounds like he's guessing. But he is right. I did read that ReiserFS had a feature called "tail packing" which allowed it to gather several small fragments of the ends of files that don't fill a block together, and put several of these tails together into one block. But there is bookkeeping required to keep track of this, and I haven't heard of any other filesystems doing it. Ext4 just might, as I've read that it has lots of new features, but I haven't looked closely at that list. 

As a rule you can assume that unused portions of a block remain unused, and therefore, lots of small files will consume more available disk space than one might expect from the sum of their sizes.

---

### Post by 3rdalbum on 2013-10-19
> **mosquetero said:**
> I am reading that ext 3 has a block size of 4 KB. What happens if I save a file that has 2 KB of size. Will the file system fill it with 2KB of zeros?

Unless filesystems have become smarter in the last fifteen years, the block size is the smallest amount you can measure a file with. A file that only has 2 KiB of data will still report as being 4 KiB, and the remaining 2 KiB of space in the block is not able to be used for anything else. If you added another 2 KiB of data to the file, it would still report as being 4 KiB and the block would be full. If you wrote another 1 KiB of data, the file would use up 8 KiB of space.

---

### Post by grahammechanical on 2013-10-19
The default file system for ubuntu is Ext4 and it has been the default for a while now. It is called a journalling file system. I have read up on journalling file systems, not that I understood much of what I was reading. But, as I understand or guess, files are saved into an area of disk called a journal and then later written to disk in the usual way in an attempt to avoid this under filling of blocks and to reduce fragmentation of data.

Regards.

---

