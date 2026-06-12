---
title: "Writing to external hard drive"
date: 2007-04-07
forum: General Help
---

### Post by lunarmelody on 2007-04-07
I have an external hard drive with a fat32 file system.  I've found I can only write to the external as root (i.e., sudo commands).  Normally this isn't a problem, but in cases where I'm trying to rip CDs or get pictures off my camera, it means I have to save them locally to my machine (since the applications themselves don't run with root permissions), and then sudo mv the files over to my external.  Does anyone know a way around this?  Thanks!

---

### Post by aysiu on 2007-04-07
Usually FAT32 external drives mount with the proper permissions. For some strange reason, yours didn't, but you can force it to:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

