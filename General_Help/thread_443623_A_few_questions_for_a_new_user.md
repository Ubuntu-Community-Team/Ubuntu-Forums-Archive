---
title: "A few questions for a new user"
date: 2007-05-14
forum: General Help
---

### Post by ajaxmanutd on 2007-05-14
A just installed Wubi on my Dell Laptop and have tried it out.  I have a couple of questions.

1.  I have an external hard drive, how do I get WUBI/Ubuntu to see the drive.
2. Can I put WUBI on my external hard drive and have it boot from that (I don't want to repartision my external hard drive)

How big of a swap file should I have,  I went from 24 gb free to less than 8 free after installing wubi.

---

### Post by ago on 2007-05-14
> **ajaxmanutd said:**
> 
1.  I have an external hard drive, how do I get WUBI/Ubuntu to see the drive.
Plug it in and it should appear in nautilus (file manager)

> 2. Can I put WUBI on my external hard drive and have it boot from that (I don't want to repartision my external hard drive)
Possibly, but you may want to have a real grub.mbr in the MBR of the removable drive to point to wubi. That is untested.

> How big of a swap file should I have,  I went from 24 gb free to less than 8 free after installing wubi.

The system drive depends on how many desktops you install. For a single dekstop environment 6GB should do. For each new desktop add ~2Gb. If you want to try a lot of programs/gamess add ~4GB.

The home drive depends on the files you want there, if you want to music/video/picture, .5 will do. 

Swap shoudl be same size as the memory if you want to hybernate otherwise .5 will do. PS since hybernation is not really very reliable at the moment you can just go for .5...

---

