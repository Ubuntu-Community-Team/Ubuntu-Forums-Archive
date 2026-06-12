---
title: "After resizing VMware disk: screwed"
date: 2007-06-21
forum: General Help
---

### Post by mschmitt on 2007-06-21
Hallo everbody,

I have a problem with my disk. Here's what I did:

- I had Ubuntu under VMWare on a Windows host.
- The size of the virtual disk (4gb) was becoming too small and I didn't find 
  vmwarediskmanager at that time
- so I created a second virtual disk, bigger (8gb), partitioned it with swap and 
  ext3.
- mounted both disks after booting from cd
- dd if=/dev/sda1 of=/dev/sdb1    copying from old to new

this worked fine and the partition manager and fdisk and fsck and every program I run 
tells: 8G, everything's fine. But: df gives still 96% full, i.e. the effective usable size of
the disk is still 4gb!? Does this mean I have a disk which is completely partitioned but only
half formatted? What did I screw up!? And how do I use the remaining 4gb of my new disk?

Help appreciated & best regards,

Matthias

---

