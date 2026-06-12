---
title: "Ubuntu VM on Macbook faster than native"
date: 2014-10-08
forum: General Help
---

### Post by ambi3 on 2014-10-08
Hello,

I found some strange problem installing Ubuntu 14.04 on my Macbook pro with a SSD and a i7 processor.

When I try to install some packages it takes forever, it's very slow especially when unpacking them, some operation that on the VM of the same operating system take 2 minutes can take up to 15 on the native installation.

Did I do something wrong? The partition is ext4, the processor and memory RW seems normal, so I'm really not understanding the reason of this slowness.

If anyone has insights on why this happens it would be great!

Thanks in advance.

---

### Post by mcparty2 on 2014-10-08
Hi Ambi,

What VM Software are you using please?

Thanks

---

### Post by tgalati4 on 2014-10-08
Software updating is slow because it requires an extensive checking of dependencies in the package database.  In a VM, this is presumably all done in RAM and faster than reading a large database from a disk.  There are some techniques to move the Debian package database to RAMdisk to make it faster, as well as trimming the database and cleaning the cache from time to time.  So I am not surprised by your findings.

What is the speed difference using:

```
sudo hdparm -tT /dev/sda
```

I bet the difference is 7 to 1 (2 minutes vs 15 minutes) between a RAM read and a disk read (even SSD).

---

### Post by ambi3 on 2014-10-09
I am using parallels 10.

@tgalati4 it can be possible, but it is still very strange because on other laptos with much lower specs than this macbook the process is faster.
That´s why I though I was missing something, maybe some driver.

The cmd you suggested me resulted as 

> 
 Timing cached reads:   29390 MB in  1.99 seconds = 14773.56 MB/sec
 Timing buffered disk reads: 1630 MB in  3.00 seconds = 542.93 MB/sec


---

### Post by tgalati4 on 2014-10-09
Wow, your buffered reads (reading from RAM) is 27 times faster than reading from disk.  So I would expect an update to be 27 times slower--however an update is probably 50% CPU and 50% disk access.  

A native install may have some issues with the motherboard/chipset that is causing a bottleneck.  This should be isolated and reported as a bug against the kernel and the specific MacBook motherboard.  It's possible that Parallels is using a compatibility mode that does not cause this bottleneck.

I only have a Powerbook (PPC) so I cannot help further as to what to investigate next.

---

