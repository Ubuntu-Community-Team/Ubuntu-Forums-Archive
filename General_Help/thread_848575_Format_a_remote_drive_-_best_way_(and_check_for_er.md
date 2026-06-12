---
title: "Format a remote drive - best way? (and check for errors!)"
date: 2008-07-03
forum: General Help
---

### Post by jessejazza on 2008-07-03
ubuntu 7.10 and 8.04

What is the best way to format a remote hard drive for backup purposes and use on windows and ubuntu. I gathered for using on both OS FAT32 was the better bet.

I used gparted - but i wanted to check for bad sectors so what can i do? From what i could gather it didn't do a FULL FORMAT like windows does - more like a QUICK FORMAT and thus no way of checking on sectors.

In 6.06 I liked the Disk Formatter which they seem to have decided to do away with - is there a replacement? - i've looked but can't spot anything.


thx
james

---

### Post by milosz.galazka on 2008-07-03
If you want to check out partition then just unmount it and run
```
dd if=/dev/partitionToCheck of=/dev/partitionToCheck
```
You could also use *bs* (like *bs=10M* ) parameter to speed up whole process

---

