---
title: "Intermittent keyboard issues"
date: 2008-05-04
forum: General Help
---

### Post by aliask on 2008-05-04
When booting, it seems there is a 75% chance that my keyboard will not work - I often have to reboot five or six times before I can log in.

The problem seems to be isolated to X - as I can switch terminals before the GDM login screen appears. The mouse also works fine.

Anyone got any ideas?

---

### Post by BuffaloX on 2008-05-04
Try to turn the power completely off (5-10 seconds),
If your keyboard works after complete power off, it's probably a bios problem.

---

### Post by matthias.sitte on 2008-05-04
I am experiencing same problems. USB and PS/2 keyboards work fine in BIOS and GRUB but when it comes to login screen it won't work. I can't, like, turn on num lock or enter any char. Switching to tty doesn't work, too. Tried messing around with "pci=noacpi irqpoll" setting but I'm not sure that helped it. Anyway, what's your hardware? My board is an ASUS A8N-SLI Deluxe one, it's crap, had different problems with it before...

---

### Post by aliask on 2008-05-04
Good to hear I'm not the only one. I'm running a Gigabyte GA-K8NSC-939 (nForce3 chipset).

---

### Post by matthias.sitte on 2008-05-05
The ASUS A8N-SLI has a nForce4 chipset. Maybe the problem is related to the nForce family?!?

---

### Post by jbman on 2008-05-05
I have an old nforce2 based board. I am having problems where the CTRL and ALT stop working after using the computer for a while, reboot fixes it. Was fine in 7.10 just 8.04, my guess its the Kernel change, I will roll back and see what happens

---

### Post by pkands on 2008-05-10
I've had this problem with any kernel >2.6.22 with all distributions.

---

### Post by matthias.sitte on 2008-05-11
Seems like the 'noapic' boot option solved the problem for me.

---

