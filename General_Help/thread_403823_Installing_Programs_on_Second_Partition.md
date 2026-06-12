---
title: "Installing Programs on Second Partition"
date: 2007-04-07
forum: General Help
---

### Post by jaymill on 2007-04-07
Basically I had an old windows partition (had a dual boot, reformatted the windows partition to ext3) that I nixed, and now I have alot more room in ubuntu. What I would like to be able to do, is install programs to that new, free partition, but for the life of me can't figure out how to do it. I don't know if this helps, but I have the permissions for that drive set up so that only my user can fully access it. Any help would be greatly appreciated.

Thank you in advance, 
Jay

:)

---

### Post by jasutton on 2007-04-07
I don't believe it's possible to install programs to the extra partition (I'm assuming you're talking about using the package installer, and not compiling your own programs from source).  I would recommend removing the extra partition, and re-sizing your root partition to fill the extra space.  This can be done easily with something like QTparted on Knoppix.

---

### Post by jaymill on 2007-04-07
could/would I loose information on either of the partitions if I use that? (I'm assuming its a liveCD)

---

### Post by zvacet on 2007-04-07
If I understand you correctly you have root and swap partition and extra one wich is also in ext3 format and it is free.If all this is correct just name your free partition your home partition.You can do it with live Cd when you came to the partition step.You will see all your partitions and for that free one give mountpoint home.

---

### Post by jaymill on 2007-04-07
thank you, I appreciate it,

---

