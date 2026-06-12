---
title: "Black Screen At Grub"
date: 2007-05-23
forum: General Help
---

### Post by taekwondodogoof on 2007-05-23
Hi,
     I'm dual-booting Ubuntu and Windows XP, and I had to recently repair XP using bootcfg and fixboot. When I rebooted, I usually have GRUB at my boot manager, but the screen stays black. I'm currently downloading a live CD to try and fix it, but is there anyway to have GRUB auto-configure itself again like when I installed Ubuntu? Thanks!

---

### Post by veerakumar on 2007-05-23
INstall grub on a floppy or cdrom.
And install from it.
Keeping a copy of grub on floppy or cdrom is handy.

---

### Post by gamer_pro_2000 on 2007-05-23
You'll need to run the live boot disc and tehn re-install grub from command line.
Here is a guide to do it:
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by hessiess on 2007-05-23
the supa grub disk can reinstall grub, without hafing to boot into a os

---

### Post by taekwondodogoof on 2007-05-23
Hey,
   Thanks for the help everyone. I followed the guide to run it from the recovery disc, but I got to the point where I ran ```
find /boot/grub/stage1
``` but after enter this I get, ```
Error 21: Selected disk does not exist
```.
     Thanks for any further help!

---

