---
title: "Easiest way to upgrade hard disk while keeping OS"
date: 2008-05-11
forum: General Help
---

### Post by Cupcake123 on 2008-05-11
Hi,

I'm currently running Ubuntu 7.10, and want to fit a larger hard disk (replacing the current one) before upgrading to 8.04.

What are the options for doing that, and are there any disadvantages to them? Currently I have two partitions, the ext3 main partition and a swap partition.

I was thinking of doing this:
 - Connect the new hard disk in addition to the existing one.
 - Boot from a Linux CD-ROM
 - Copy all data from the old disk to the new disk using e.g.    dd if=/dev/sda of=/dev/sdb
 - Use a partition manager tool to move and resize the swap    partition on the new disk, and enlarge the ext3 partition.
 - Power down, disconnect old hard disk.

Is there anything else to consider? If that method works, a disadvantage is that any current file fragmentation would be present on the new disk.

Alternatively, could I partition the new disk, then use tar with appropriate options to completely duplicate the directory tree, so the system would boot and all apps work?

---

