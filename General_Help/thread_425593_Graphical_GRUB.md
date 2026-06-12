---
title: "Graphical GRUB"
date: 2007-04-27
forum: General Help
---

### Post by stchman on 2007-04-27
Hello all, GRUB for Ubuntu is kind of boring.  Is there a spiffy graphical version?

---

### Post by disturbedite on 2007-04-27
i'm not sure what you mean, grub is graphical with *buntu  (afaik)  unelss you're like me; i formatted and reinstalled with feisty this time and grub isn't graphical because i only have one kernel version/partition to boot to, so hence no choice needs to made.

---

### Post by x1a4 on 2007-04-27
Hi,

_/boot/grub/menu.lst_ contains an entry that's something like this: 

**splashimage=(hd1,0)/boot/grub/splashimages/gnulinux.xpm.gz**

(hd1,0)/boot/grub/splashimages/gnulinux.xpm.gz

is a 640x480, 16-colour, gzipped x-bitmap, in this example residing on drive 1 (second drive) partition 0 in _/boot/grub/splashimages_ and is named _gnulinux.xpm.gz_.  

You can create the image yourself or install the **grub-splashimages** package 

*sudo aptitude grub-splashimages*

and use one of the images in that package:

---

### Post by spone on 2007-04-27
> **x1a4 said:**
> *sudo aptitude grub-splashimages*
try adding install to that line ;)

---

### Post by x1a4 on 2007-04-27
My bad

*sudo aptitude **install** grub-splashimages*

Thanks spone

---

