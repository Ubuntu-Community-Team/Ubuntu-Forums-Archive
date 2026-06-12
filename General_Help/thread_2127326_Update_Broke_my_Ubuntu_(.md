---
title: "Update Broke my Ubuntu :("
date: 2013-03-19
forum: General Help
---

### Post by FabulousCabbage on 2013-03-19
Ok so after successfully installing the proprietary amd catalyst drivers, i rebooted and made sure everything worked, and it did, but after updating my system using the standard Ubuntu software updater, it keeps booting into "low graphics mode" and giving me errors saying it can't detect my video card and all that caper, i'm pretty sure i saw an xorg update while it was updating and i think that may have mucked up my drivers, i'm not sure.
Anyone know how to fix this?

I'm using Ubuntu 12.10.
XFCE4

My Computer specs:

AMD FX8350 8 core cpu
16GB Crucial ballistix sport at 1600mhz
Gigabyte HD7870 OC
Asus M5A97 LE R2.0  motherboard.

---

### Post by arpanaut on 2013-03-19
> Ok so after successfully installing the proprietary amd catalyst drivers

With that method of installing drivers, with each kernel and/or xorg update you will need to reinstall your chosen drivers.
If you use the drivers available through Ubuntu's repositories, the drivers will get updated automagically.

---

### Post by FabulousCabbage on 2013-03-19
I installed them using the package downloaded from the amd website, i fixed the problem by installing the open source drivers and was worried that the proprietary drivers would cause problems again, but now i know this i'll reinstall the proprietary ones as i found they were a bit less buggy and performed alot better.

thank you

---

