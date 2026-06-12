---
title: "Dual Booting Two Harddrives (Both linux)"
date: 2006-11-23
forum: General Help
---

### Post by jackyyll on 2006-11-23
How do you dual boot two different hard drives which are both running linux (Ubuntu 6.1 on Master and SuSE 10 on slave)? Is there anything special I have to do to set up GRUB to let me switch between the two, or anything that i need to set up?

---

### Post by jimbob on 2006-11-23
You need to be a little more specific - tell us what is on each partition of each drive and which is master etc.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jackyyll on 2006-11-23
Well the first hard drive right now has Ubuntu 6.1 on it, and the second hard drive is empty :s

---

### Post by jackyyll on 2006-11-23
Anyone? :s

---

### Post by Ocxic on 2006-11-23
just install ubuntu normally it should detect the current ubuntu installation during the "install grub" part of the installation and add itself to your current setup. if not, pm me, or msg back here and someone will help you modify your "/boot/grub/menu.lst" file so you'll be able to boot both.
Even better if you are using a seperate partition for your "/boot" directory, then just use that for the new system as well, i believe. no worries, be happy

---

### Post by Azakus on 2006-11-23
Grub will auto switch between the two drives if you write the menu.lst option the right way.
Post your menu.lst file and which drive has what version. You'll find it under /boot/grub/menu.lst.

---

