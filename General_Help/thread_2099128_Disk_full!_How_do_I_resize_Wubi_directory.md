---
title: "Disk full! How do I resize Wubi directory?"
date: 2012-12-28
forum: General Help
---

### Post by zesterer on 2012-12-28
Hi,

The title is pretty much self-explanatory - I installed Ubuntu with Wubi, and I have now run out of disk space in /home. I don't want posts telling me to clean up my files, I have done that already. Thanks.

The directory /dev/loop0 is full. I'm a bit of a beginner to linux and Ubuntu, so I dont know how to fix this. I've searched around a lot, and tried several solutions including wubi-resize_1.5b.sh, and I got this from the "sudo bash wubi-resize.sh 10" command:

[COLOR="Blue"]wubi-resize.sh: The new size (10 GB) isn't sufficient to hold your
wubi-resize.sh: existing install (17 GB) plus a freespace buffer[/COLOR]

What does this mean, how can I fix it, and are there any other ways I can resize my /dev/loop0 so that I can have more space? I have already resized the partition, I just don't know how to increase the size of the /dev/loop0 directory to fill it... :S

Thanks for all replies,

Barry Smith

---

### Post by Mark Phelps on 2012-12-28
Wubi installs do not create separate partitions; instead, they create a virtual filesystem inside an existing Windows NTFS partition.  Thus, they can't be resized in the same manner that you would resize a partition.

The Wubi guide (linked below) has instructions for resizing the filesystem:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by zesterer on 2012-12-28
Thanks! Very helpful, I think this is what I wanted!

:)

---

