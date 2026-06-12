---
title: "Bootable iso with k3b"
date: 2007-01-09
forum: General Help
---

### Post by Iarwain ben-adar on 2007-01-09
Hiya!

Trying to install Sorcerer Linux on my vmware server, i downloaded the "grimoire",
and tried burning it to iso.

Problem is, i can't boot from it :?

How can i make vmware boot from this iso?


Iarwain

---

### Post by cmost on 2007-01-09
First, make sure your ISO is really a bootable image.  Are you using VMware player, workstation, or server?  In workstation or server, simply edit the guest operating system, add CD / DVD device, choose ISO image instead of physical device and make sure it's the only device (i.e., either delete the physical device or change the physical device to use the ISO.)  Power on the virtual machine and you'll be booting from the ISO.  If you want to get fancy, you can go into the virtual machine's BIOS (I think it's press F1 when powering on but i'm not sure) and make sure the CD / DVD device is the first boot device; just like a real computer.  Good luck!

---

### Post by Iarwain ben-adar on 2007-01-09
Ok,
shame on my :?

Whilst typing an answer and checking what files i downloaded,
i realised that i iso'd the wrong file :oops:

Thanks for the answer anyway ;)


Iarwain

---

