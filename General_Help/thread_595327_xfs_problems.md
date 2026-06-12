---
title: "xfs problems"
date: 2007-10-28
forum: General Help
---

### Post by HackerBaloo on 2007-10-28
I installed a new hard drive on my Ubuntu 7.10 server.  And  I decided to try xfs, and to use the disk as home partition. Started to copy about 100 GB data over the network, from my windows desktop machine.Good performance, 7 - 8 Mbytes /s so the network seemed to be the the bottleneck.

But then I just lost contact with server, and in the kernel.log I later found this:
"XFS internal error XFS_WANT_CORRUPTED_GOTO at line 1563 of file /build/buildd/linux-source-2.6.22-2.6.22/fs/xfs/xfs_alloc.c.  Caller 0xd0afe323"

I restarted continued the copy, and it happened again, so I started over with jfs, and it does not perform as well as xfs when I copy, I only get about 4 MByte/s, but no crashes.

I would of course like the performance of xfs and the stability of jfs, could I get that :o)

I installed gparted,xfsprogs and jfsutils. And then I created the partitions with gparted. 
Nothing special in fstab I think:
#/dev/sdb1       /home           xfs       defaults  0      2
/dev/sdb1       /home           jfs       defaults  0      2

---

### Post by kelvin spratt on 2007-10-28
I was going to use XFS for 7.10 but i got a warning when I went to format, So I used JFS. and I get really good speeds to my wifes laptop and back, also file transfer speeds to my external drives have doubled, the boot up time is also very fast about 35  secs before about 60 secs. I have learned that things that work for me might not work for others and vice versa..

---

### Post by kerry_s on 2007-10-28
can you switch kernels, i'm a summing your using the generic 1, have you tried the i386, i686 ?

---

### Post by HackerBaloo on 2007-10-29
I will try a better kernel, i believe there are an AMD one too?

---

