---
title: "gparted?"
date: 2005-06-03
forum: General Help
---

### Post by not_yet on 2005-06-03
I'd like to use gparted to partition my drive, but I can't seem to get started?

anyone know of a tutorial or howto for this

thanks

---

### Post by az on 2005-06-03
If you have a mouted partition on the drive, you cannot partition it.  Use a live cd like the installer cd to patition:

[http://test.wiki.ubuntu.com/forum/installation/Partitioning](http://test.wiki.ubuntu.com/forum/installation/Partitioning)

Stop after you have resized....

---

### Post by haiku72 on 2005-06-21
I have the same problem, gparted launches then dies suddenly.  I launched it from commandline with root previliges and it returns: segmentation fault.

Ok so no mounted partitions your say?  But I tried qtparted and that works just fine.  It's a pitty as I want to avoid using QT or KDE apps in my setup.  Anyone has an idea how to fix this?

regards

---

### Post by afonic on 2005-06-21
>  
If you have a mouted partition on the drive, you cannot partition it. Use a live cd like the installer cd to patition:

[http://test.wiki.ubuntu.com/forum/i...on/Partitioning](http://test.wiki.ubuntu.com/forum/i...on/Partitioning)

Stop after you have resized.... 


I am not sure this is correct all the time. I had a 40GB NTFS partition on the disk that / and /home was mounted and using Gparted I deleted it and created a new linux partition.

Remember you need to mount it manually afterwards (add it to the fstab file as well).

---

