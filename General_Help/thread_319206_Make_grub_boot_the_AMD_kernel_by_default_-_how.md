---
title: "Make grub boot the AMD kernel by default - how?"
date: 2006-12-15
forum: General Help
---

### Post by Aramis on 2006-12-15
Hi y'all,

up until recently I had several kernel-image available on my AMD Duron Laptop. In a past few day, I was provided with a brand new kernel image. I removed up the old ones just to discover that GRUB does not boot the custom AMD image at start-up. I have to press ESC at boot time and select manually the kernel I want.

My question is thus simple.

What do I have to do to make grub boot the latest AMD Duron Kernel Image by **default**? I have searched for tutorials, and through wikis without success.

Help much appreciated,

Ar@mi$

---

### Post by an.echte.trilingue on 2006-12-15
Edit the file /boot/grub/menu.list

find the line that says default="" and change that to the number in the menu that you want it to boot by default.

You will have to repeat this each time a new/updated kernel is installed.

Take care,
-mat

---

### Post by Aramis on 2006-12-15
Hi there,

thanks for the tip. I have to say I found the manip less than straigth forward, and I have to add that I was shown this custom kernel right after I installed Ubuntu on my laptop, and for some reason the method that was shown to me seemed easier, like "update-grub" was enough or something.

in any case it works!

until next time, thanks a bunch.

Ar@mi$

---

