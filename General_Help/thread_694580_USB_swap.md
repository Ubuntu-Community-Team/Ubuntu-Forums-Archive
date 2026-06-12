---
title: "USB swap"
date: 2008-02-12
forum: General Help
---

### Post by dougleduck on 2008-02-12
I've been running out of memory when trying to run a Matlab program. 

I've read quite a lot of conflicting advice with regards to using a USB drive to add SWAP space.

I have 512 MB RAM and 1.3GB swap space currently which isn't enough to run this program.
I only need to use it occasionally, to let it run then go back to normal swap space.

I need a few things clarified

Would I be able to use hard disk swap and USB space simultaneously?
Does the faster search time of USB make up for it slower read and write speed?
(It may be relevant that I need the memory to load a large matrix and the write another large matrix)
People have referred to limited read/write cycles. Does anyone have any grasp of how long a drive would last? Id probably only need to write once a day and the program runs for around 1 hour.
Does anyone have any experience of this and how long did it last/what was performance like?

---

### Post by az on 2008-02-12
> **dougleduck said:**
> 

Would I be able to use hard disk swap and USB space simultaneously?

Yes.  You can set up a number of different swap files or spaces.

> **dougleduck said:**
> 

Does the faster search time of USB make up for it slower read and write speed?

A USB drive is faster than a SATA drive?  I don't think so.  There is a lot more overhead to a USB thumb drive than a SATA hard disk.

> **dougleduck said:**
> 
People have referred to limited read/write cycles. Does anyone have any grasp of how long a drive would last? Id probably only need to write once a day and the program runs for around 1 hour.
Does anyone have any experience of this and how long did it last/what was performance like?

Sure, the Nand memory has a limited lifetime, but the device's controller will cycle through the cells to minimize the reuse of each individual cell.  This is part of the overhead that a USB drive requires.  

It has been calculated that a common sized NAND USB drive would require more than fifty years of continuous writing to reach the suggested limit of write cycles to risk failure.  So, you're safe.

You can just use a swap file, though. ([http://linux.die.net/man/8/mkswap](http://linux.die.net/man/8/mkswap))

dd if=/dev/zero of=swapfile bs=1024 count=65536
(you probably need a lot bigger than that)

sudo mkswap swapfile

sudo swapon swapfile

---

### Post by dougleduck on 2008-02-12
I didn't realise you could make a file to use as swap. Unless my need gets really desperate that sounds like a much better solution. Thanks!

---

