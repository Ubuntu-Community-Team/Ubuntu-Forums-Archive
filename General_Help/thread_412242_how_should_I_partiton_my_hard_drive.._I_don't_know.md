---
title: "how should I partiton my hard drive.. I don't know what to do."
date: 2007-04-17
forum: General Help
---

### Post by billdotson on 2007-04-17
I used gparted to make some partitions on my internal hard drive before I installed Windows.  Now in Windows I am getting some weird errors.   I think I might have an error in the partition table.  Should I wipe the entire drive , install Windows and then do the other partitions or should I do the other partitions first?  I have heard of someone writing zeros to their hard drive.. what does that mean

Thanks

---

### Post by konungursvia on 2007-04-17
It depends if you have files or data you want to keep.  If so, just delete the newer partitions, and resize the oldest windows one to be the full drive, and run windows, it should try to scan its disk and repair itself, you might save lots of your data this way. If there was nothing you really wanted, you could reformat and re-install, if you really wanted to get rid of the apparent errors. Maybe people could help more if you gave details on the sizes of your partitions, when you made them, what are their file systems, did you defragment the windows partition several times before using gparted, etc.

---

