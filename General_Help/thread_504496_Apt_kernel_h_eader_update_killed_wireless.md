---
title: "Apt kernel h eader update killed wireless"
date: 2007-07-19
forum: General Help
---

### Post by petersra on 2007-07-19
Hi,

Last night Apt updated the kernel header files.  However, after the install and a boot, my wireless is dead.  I use ndiswrapper.  Is there a way to back out these updates?:(

---

### Post by petersra on 2007-07-19
Sorry, I am on Edgy.  For what its  worth, I was using Feisty  on my thinkpad T23 but suspend/resume did not work so went back to Edgy.

---

### Post by Ayuthia on 2007-07-19
You should be able to go into /boot/grub/menu.lst and have it point back to the previous kernel version.  

By the way, have you tried to remove ndiswrapper and put it back in?  If that does not work, have you tried to recompile ndiswrapper?

---

