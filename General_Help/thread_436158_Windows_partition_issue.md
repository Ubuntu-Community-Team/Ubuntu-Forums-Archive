---
title: "Windows partition issue"
date: 2007-05-07
forum: General Help
---

### Post by Muzer on 2007-05-07
I have two hard disks, one of which has one partition and runs no OSs, I'll call this HD1. The other of which has three partitions (one is swapfile) and runs (K)Ubuntu Edgy (as I type being updated to Ubuntu Feisty) and Windows XP Home on seperate partitions. I'll call these HD2A (for Edgy) and HD2B (for XP). When I first installed it I had a problem that it couldn't detect HD2B, but it detected HD1 and HD2A. I later resolved this using a mounting tutorial, the trouble is it'snot displayed in /media (Kubuntu) or Computer (Ubuntu), only in /mnt, which is a pain. The other thing is, if Windows XP is hibernated and I start Ubuntu, HD2B doesn't mount, and if I mount it manually the contents appear as blank. Is there any way I can fix these two problems?

---

### Post by rich.bradshaw on 2007-05-07
If hibernate Windows it won't let you mount it as this would likely corrupt the filesystem - Windows doesn't unmount it when it hibernates. So you can't fix that aprticulatr thing.

---

