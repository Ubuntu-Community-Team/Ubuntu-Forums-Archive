---
title: "Compiling GRUB 0.97 on Ubuntu Feisty Results in Seg Fault"
date: 2007-04-28
forum: General Help
---

### Post by Computer Guru on 2007-04-28
Compiling GRUB 0.97 from source:
```
cd grub
./configure
make
sudo make install
grub
```

It'll configure, make, and install OK, but:
```
cg@Aurora:~$ grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version /boot/grub/default  (128K lower / -1213591848K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
Segmentation fault
```

Any clues? I can use the deb just fine, but I'm making some modifications to GRUB trying to figure out just what exactly gives some users the "GRUB" text in the upper-left corner when attempting to dual-boot with Vista via [EasyBCD](http://neosmart.net/dl.php?id=1)

*Edit*
I should probably add that this happens with a stock GRUB on a stock Feisty as well, without any of the afore-mentioned modifications to the code.

---

### Post by Computer Guru on 2007-04-29
Any ideas?
It's rather important..... thanks :)

---

### Post by andrewdodd13 on 2008-01-26
I'm having this same problem on Gutsy. Can't find any good reason for it either.

---

