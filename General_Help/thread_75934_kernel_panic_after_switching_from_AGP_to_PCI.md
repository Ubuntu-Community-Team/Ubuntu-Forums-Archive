---
title: "kernel panic after switching from AGP to PCI"
date: 2005-10-14
forum: General Help
---

### Post by jackmacokc on 2005-10-14
I am playing around and switched from an AGP ATI Rage 128 card to a PCI Nvidia Geforce2 card. Now i'm getting a kernel panic - not syncing: fatal exception in interrupt. 

I'm assuming this has to do with IRQ assignments or something.

Any ideas on what I can do? I'd like to try and fix it rather than re-install..for learning sakes.

---

### Post by Comp_Lex on 2005-10-14
I'm experiencing the same problem. It seems that this bug is related to the kernel. This problem is occuring with the other major distro's as well...:( :mad: 

I've entered a bugreport about this. You can find it [here](http://bugzilla.ubuntu.com/show_bug.cgi?id=14712)

---

### Post by siennalizard on 2005-12-25
I'm getting the same error on boot, after letting my Ubuntu Breezy update the kernel to 2.6.12-10-686. I hacked around and managed to set up the -386 kernel (same version), but that just freezes after a random amount of time, and always crashes before I can fully install the modules for the -9-386 kernel. Very frustrating, and an entirely automated update that did it!

J.

---

