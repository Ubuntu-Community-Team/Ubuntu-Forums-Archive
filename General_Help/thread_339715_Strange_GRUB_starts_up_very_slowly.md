---
title: "Strange: GRUB starts up very slowly"
date: 2007-01-16
forum: General Help
---

### Post by manishk on 2007-01-16
I have a dual boot (Edgy/XP) on my laptop (HP nx6325). 

I face this strange problem, and its irritating:

When I boot (both hot and cold) my computer the GRUB menu turns up much faster if I had used XP in the last session and if it was Edgy the boot up is considerably slowed done.

And occasionally, if the last session was Edgy, the keyboard stops responding when the GRUB menu shows up!!

---

### Post by wolfchri on 2007-01-24
Manishk,

the reason is the faulty BIOS of the NX6325 - it suffers from the bad state issue, a problem well known with several other HP notebooks.

As a work around, just un-load the psmouse module before rebooting or shutting down.

See my NX6325 How-To (Nr. 6 / Hibernation) for details how to automate this in the respective scripts.

[http://vale.homelinux.net/wordpress/?p=106](http://vale.homelinux.net/wordpress/?p=106)

---

### Post by manishk on 2007-02-04
I had somehow overlooked that...thanks a lot

---

