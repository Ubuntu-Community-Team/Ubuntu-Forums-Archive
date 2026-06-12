---
title: "Xserver won't start with Radeon X300"
date: 2007-03-20
forum: General Help
---

### Post by Falkon on 2007-03-20
I put a "new" Radeon X300 in my box today (taken from an older comp), and when I loaded Ubuntu from Grub it said that the Xserver failed to start.  I'm positive this is because of the graphics card, but I have no idea how to fix it.

As far as I know, I CANNOT disable onboard graphics from the BIOS.  I looked but couldn't find the option, and I even called Asus only to have them tell me that it was absolutely impossible to disable the onboard.  They said it would happen automatically when I put a new graphics card in (which it did for windows), but either it didn't for Ubuntu, or I have some other graphics-related problem.

Please help asap!

---

### Post by Bastanteroma on 2007-03-20
Try running "sudo dpkg-reconfigure xserver-xorg" from the command line (choose failsafe at the grub menu) then okaying all the options (Choose "simple" to see the least options at the monitor config stage).  If that works, from within X you can follow these instructions to install the binary fglrx driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29)

---

### Post by Falkon on 2007-03-21
Ok, I did that and it works fine now.  Thanks!

---

