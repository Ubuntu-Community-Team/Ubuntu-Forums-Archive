---
title: "How to adjust XFS pagesize and block size?"
date: 2008-05-20
forum: General Help
---

### Post by Fox5 on 2008-05-20
Hey all,
I'm currently running Ubuntu on a 32GB transcend compact flash card. After checking out benchmarks on the web (and running a few of my own), it would appear that throughput increases with block size. Additionally, it increases significantly up to the physical block size of the device being used. Transactions per second are maximized by matching block size to physical block size (throughput however appears to go up faster than transactions/s drops past this point however).

Currently I have an XFS file system with 4KB block sizes. I would like to grow the block size if possible, and am willing to reformat if necessary. However, the XFS man page notes that the max block size is limited to the page size, which I believe is 4KB by default. So I would like to change both.

I suppose I could switch to another file system (the larger block size = better performance on flash drives should hold for any file system I suppose), but XFS appears to allow for the largest block sizes. I don't know the block size of my 32GB card, but I'd guess at least 16KB, and a very good possibility of being higher. (wouldn't be hard to test with the right software but I'd rather not destroy the drive data until I know this is something that can be done)
Besides that, apparently both XFS and Reiser (with tailpacking enabled) have the ability to store multiple files within a block (and only these 2) if they're smaller than the block size. I don't believe reiser allows for very large block sizes anyway, and even XFS seems to only go up to 64KB.

Actually, reading up a bit more on it, it appears that the pagesize limit is set in the linux kernel (can it be changed?) and effects all file systems that can go above 4k block sizes, not just XFS. So that would include Reiser and the FATs (and maybe NTFS?) as well.
Hmm, if that's the case, I wonder if there's anything that can be done to improve performance? For whatever reason, my windows 2000 virtual machine with superfetch and lazy transactions just flies without any of the lag of ubuntu, which I guess is the result of delaying all transactions until absolutely necessary (shut down or out of memory) and the i/o abstraction done by the virtual machine. Anyway to achieve the same effect on Ubuntu in that case?

---

