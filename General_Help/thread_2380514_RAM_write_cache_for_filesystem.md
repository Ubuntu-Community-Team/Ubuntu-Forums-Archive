---
title: "RAM write cache for filesystem"
date: 2017-12-18
forum: General Help
---

### Post by syadnom on 2017-12-18
I have a couple of process that write out small files but often as many as 20 at a time (Security Cameras).  This causes IO issues as random writes and even a fast drive like the WD Reds I'm using can't keep up.  Basically it's 20x5Kbps or less, ie <=12.5MBps but random writes.

On windows, I'm able to use a program called PrimoCache which solves this perfectly.  Writes come in to RAM, then after a set period the are written as a sequential write.  This program allows me to put 4x as many cameras on a drive, it's amazing.

I can't find this for linux.  I've been playing with using aufs and a ramdrive and an rsync task in the background to move from RAM to HD.

I understand the pitfalls, if the computer is shut off I loose data, but that's ok because that loss doesn't cause any errors and losing <30 seconds of video on the very rare occasion there is a power outage is of no impact.

I absolutely hate having to run larger systems on Windows because of performance issues, but this is that corner case where it's true, and the cost to add a bunch more spindles and do a RAID10 is substantially higher than a windows and primocache license.

So, any ideas here?   A write-deferred RAM cache for ubuntu?

---

### Post by mikewhatever on 2017-12-18
You can try tweaking some of the following parameters:
```

vm.dirty_background_ratio
vm.dirty_background_bytes
vm.dirty_ratio
vm.dirty_bytes
vm.dirty_writeback_centisecs
vm.dirty_expire_centisecs

```

Here is a good write out on what each one is: [https://lonesysadmin.net/2013/12/22/better-linux-disk-caching-performance-vm-dirty_ratio/](https://lonesysadmin.net/2013/12/22/better-linux-disk-caching-performance-vm-dirty_ratio/).

---

### Post by Autodave on 2017-12-18
Can you provide us with some specs on the machine you are using? What version of Ubuntu are you using?

---

### Post by syadnom on 2017-12-22
i5-2400, 8GB (can be upgraded to 16GB), OS on a 120GB SSD, storage is WD RED 8TB.

vm tuning doesn't work for multiple reasons.  The default dirty ratios are already very generous for the need at ~800MB.  Altering the writeback to a long number pushes the write commits off for a while, but if I push this out to say 30 seconds, that's system-wide and means the database and other important data may not be written to disk.  Big difference losing a few seconds of video data when the power drops vs corrupting a database (VMS software often runs mysql or mongodb).

Basically tuning the vm enough to work is extremely risky.

---

