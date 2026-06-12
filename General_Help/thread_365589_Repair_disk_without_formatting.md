---
title: "Repair disk without formatting?"
date: 2007-02-19
forum: General Help
---

### Post by ~LoKe on 2007-02-19
fdisk seems to indicate that there's a problem with my /home partition.  I'm having some problems that must be caused by this (fresh install, with my old /home partition mounted).  I'd like to repair the partition, if that's possible.

I'm contemplating backing up all my data and just starting fresh, but I've got quite a bit of stuff that would take a massive amount of DVD's to get it done (I have plenty, but seems like a waste).

Do I have any viable alternatives?

---

### Post by bikeboy on 2007-02-19
You could run a livecd, Ubuntu or Damn Small Linux so that your partitions aren't mounted. Then you can get fdisk to attempt repair. Backing up is still a good idea just in case the errors are unfixable.

"man fdisk" explains the options available and using a livecd is easier than trying to unmount your partitions, especially root.

---

