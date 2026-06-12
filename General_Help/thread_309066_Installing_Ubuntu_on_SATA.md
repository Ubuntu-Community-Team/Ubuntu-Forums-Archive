---
title: "Installing Ubuntu on SATA"
date: 2006-11-29
forum: General Help
---

### Post by Globox on 2006-11-29
Hey there. I have three hard drives in my computer (two SATA, one IDE). The first hard drive (SATA) is my dedicated Windows XP drive, it is a single primary partition dedicated to running Windows XP. The second hard drive (SATA) I want to be my dedicated Ubuntu drive  (my partition scheme looks like this: primary partition for "/", logical partition for "/home", logical partition for "/swap".) The third and final hard drive is an IDE drive formatted in ext3 and consists of one primary partition (for data storage).

Here's my trouble: when I first installed Ubuntu it went fine, except for the installation of Grub: it installed on the IDE drive. Now, in order to get into Ubuntu/Windows I have to select their drive in the BIOS as the first boot, or boot from the IDE drive.

How do I get Grub to install on the Ubuntu SATA drive (I'm going to switch the cables to that the Ubuntu drive is in the #1 SATA slot, making it my primary drive and the Windows XP drive secondary).

---

### Post by smoker on 2006-11-29
if it is no problem to reinstall ubuntu, then the easiest way would be to temporarily disconnect your ide drive, reinstall ubuntu, then connect the ide drive again after.

---

