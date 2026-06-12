---
title: "Swapping GPU drivers Quick and easy?"
date: 2014-03-06
forum: General Help
---

### Post by curtis6 on 2014-03-06
Is there any quick and easy way of switching from/to "Radeon Open source" Drivers to "FGLRX proprietary" drivers?
I ask because Like computer runs 70 degrees cooler with the Open Source Drives, but some games that i'm trying to run /w Wine required the Proprietary.

---

### Post by mörgæs on 2014-03-08
Which Radeon card and which version of Buntu?

---

### Post by curtis6 on 2014-03-09
> **mörgæs said:**
> Which Radeon card and which version of Buntu?
Radeon Mobility 5370 and 12.04.3

---

### Post by Mark Phelps on 2014-03-09
If you're talking about a quick way to switch back and forth between the two sets of drivers, as far as I know, NO.

---

### Post by monkeybrain20122 on 2014-03-09
I know for Nvidia you can just remove xorg.conf and reboot to revert to nouveau and run sudo nvidia-xconfig to switched back to Nvidia. Tested it with 13.10 and Nvidia 331 installed from xorg-edgers. I was surprised as I didn't expect it to be so easy. Not sure if something similar works for AMD.

---

