---
title: "Broken Grub, no cdrom"
date: 2006-11-19
forum: General Help
---

### Post by sendas on 2006-11-19
I have a headless Ubuntu file server where after I got ubuntu installed I took out the cdrom and added another hard drive to the LVM. I do however have a floppy drive installed.


 The problem
I installed dhcp3-server and did a remote but it never came back online. Plugged a monitor into it and it keeps freezing saying grub loading please wait. the only change I made to the server was installed dhcp3-server.

Is there a way to fix grub without a cdrom?

---

### Post by Herman on 2006-11-19
Hello sendas, What about a Super Grub Floppy disk to get you booted up to begin with, [sgd_0.9528_english_floppy.img.bz2]("http://forjamari.linex.org/frs/download.php/447/sgd_0.9528_english_floppy.img.bz2")
Then you should be able to fix Grub when your system is up and running.
How Make your Super Grub Floppy Disk................................................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk")

if you want to make your own personal Grub floppy for your convenience, here is my recipe for one, [Click here]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make").

---

