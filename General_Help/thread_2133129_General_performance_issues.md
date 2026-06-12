---
title: "General performance issues"
date: 2013-04-07
forum: General Help
---

### Post by maslowk on 2013-04-07
So after having not used ubuntu since about 2008 I've recently decided to give it another go. Unfortunately however I've been having some serious with performance in general.

When attempting to boot from a flash drive it generally takes somewhere in the neighborhood to get from the POST to the desktop. Once I do make it to the desktop everything interface wise is incredibly sluggish and generally unresponsive. What I find strange is that no other linux distro I've tried from USB on the same laptop with the same thumb drive have this problem. 

I've tried a handful of different versions between 10.04 and the most recent release, including both the LXDE and XFCE spins, as well as different editions of linux mint. Here are the laptops relevant specs;

**Video**: Mobile 915GM/GMS/910GML (32mb vram)
**CPU** Intel Pentium M processor @ 1.73GHz
1024mB ram

Anyone have any idea what might be causing the issue?

---

### Post by BmanTheBoss on 2013-04-07
Try making a boot disk. I was never able to get Ubuntu to work on a flash drive, so try burning the Ubuntu .iso image to a cd, I found this usually works better.

---

### Post by Frogs Hair on 2013-04-07
Your video ram looks low for newer versions of Ubuntu . If 10.04 is sluggish any version after that will be even more so. Lubuntu uses the least resources of all the flavors.

---

### Post by maslowk on 2013-04-08
> **BmanTheBoss said:**
> Try making a boot disk. I was never able to get Ubuntu to work on a flash drive, so try burning the Ubuntu .iso image to a cd, I found this usually works better.

For the sake of saving resources (or lack thereof) I suppose I could try doing a straight install/WUBI, see if either work better.

> **Frogs Hair said:**
> Your video ram looks low for newer versions of Ubuntu . If 10.04 is sluggish any version after that will be even more so. Lubuntu uses the least resources of all the flavors.

The problem here is that *every* flavor of Ubuntu I've tried on this particular hardware has the same issue, including Lubuntu, with all of them being (subjectively) equally sluggish. RAM consumption and CPU load are all normally within reasonable levels as well, which makes me think if vram is an issue the overhead must be coming from something else unique to ubuntu. 

I just find it strange that it's strictly Ubuntu-based distributions that have this issue regardless of what DE/WM they're using, when any other debian based distro I've used (normally XFCE/LXDE based) seem to work perfectly fine in this respect.

---

