---
title: "Edgy &amp; Grub - help!!"
date: 2006-12-03
forum: General Help
---

### Post by Bonez56 on 2006-12-03
Hi all

I have a fairly new 320gb sata HDD.
Up until this afternoon, I had a vista beta installed. I removed the partition holding Vista and re-allocated the space during the ubuntu install to use as linux.

I also have a 120gb IDE drive in my PC which grub calls (hd0) - the SATA drive is called (HD1)

So, I've tried installing grub on both (HD1) and (HD1,0) as well as (HD1,1) but no matter what I do, I get a grub error 22: No such partition - when trying to boot.

Can anyone assist? I've installed ubuntu heaps of times in the past on my IDE drives but never experienced this problem.

Thanks

---

### Post by Sef on 2006-12-03
This is GRUB error 22:

> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by bulldog on 2006-12-03
You installed it on the Sata,(hd1)and (hd1,0) are both the Sata,(hd1,1)is the  second partition on the Sata disk.
But did you have a look on the IDE disk?

When you boot from the Sata it's called (hd0) and the IDE becomes (hd1)
So it all comes to what disk you use to boot.

---

