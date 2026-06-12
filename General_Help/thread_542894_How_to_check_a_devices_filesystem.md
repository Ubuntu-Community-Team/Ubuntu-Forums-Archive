---
title: "How to check a devices filesystem"
date: 2007-09-04
forum: General Help
---

### Post by torusturtle on 2007-09-04
Hi

I'm having a disc that I build out of a FAST VCR (Bluewin TV300).
I can see the partitions in /dev/ but I can't mount them because I don't know wht kind of filesystem they used. Is there a way or maybe program that helps determing the used filesystem?

I have Ubuntu 6.06 LTS installed.

Thanks for your help!

---

### Post by geraldm on 2007-09-04
man mount

try with proper substitutions:
mount -t auto /dev/{device} {mountpoint}

Gerald

---

### Post by rscott5 on 2007-09-04
```
sudo fdisk -l
```

That will list all disks connected and there is a column for the filesystem type.

---

### Post by ayoli on 2007-09-04
or another one a bit more friendly in a terminal:
```
sudo cfdisk
```
or if you prefer the graphical way you may want to try gparted
if it is not installed on your system:
```
sudo apt-get install gparted
```

---

