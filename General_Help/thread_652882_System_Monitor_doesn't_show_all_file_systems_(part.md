---
title: "System Monitor doesn't show all file systems (partitions)"
date: 2007-12-29
forum: General Help
---

### Post by RyanGT on 2007-12-29
I really like the File Systems tab in the Systems Monitor as a way to check how full my partitions are.  For some reason, one of my gutsy machines doesn't show the root partition.  It only shows my fat32 partition.  I have another machine that I think has nearly the same partitioning scheme that shows everything (except NTFS, which is to be expected).

How can I get my root partition back into the System Monitor?

Thanks,

Ryan

---

### Post by Woody1987 on 2007-12-29
open up system monitor, goto edit->preferences->file systems

check show all filesystems. All the partitions should now showup including any ntfs partitions you may have.

---

### Post by RyanGT on 2007-12-29
That shows me /var, /sys, /proc, and /dev, but still not root (/) or NTFS.

---

### Post by RyanGT on 2007-12-29
Apparently the problem is that I have been running for quite some time with a bad fstab file.  It never specifies the root partition.  I didn't even know it was possible to boot without a valid fstab.  Once the fstab file specified the root partition, the partition shows up in the system monitor perfectly.

Ryan

---

