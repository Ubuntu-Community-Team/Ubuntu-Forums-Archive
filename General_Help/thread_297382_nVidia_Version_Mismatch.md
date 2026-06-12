---
title: "nVidia: Version Mismatch"
date: 2006-11-11
forum: General Help
---

### Post by bobpaul on 2006-11-11
I installed the 9625 version of the nVidia driver from the nVidia website, but it didn't work. I tried to uninstall it and install from 8776 from the repos, but now it's telling me:

```
(EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0):     NVIDIA GLX module.  X driver version: 1.0-9625; GLX module
(EE) NVIDIA(0):     version: 1.0-8776.  Please try reinstalling the NVIDIA
(EE) NVIDIA(0):     driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***

```

I did a ```
find / | grep 9625
``` and deleted some *.so files a week ago and the 8776 driver started to mostly work (twinview, but no DRI). 

However, today I tried to reinstall the 8776 driver again (to get DRI) and the problem resurfaced. ](*,) Now I have no files on my system that have 9625 in the name and no idea where this remnant 9625 X driver might be hanging out that's causing the problems. Right now I can only start X if I use the nv driver and then I don't get dual screen.:(

---

### Post by OffHand on 2006-11-11
Try this: [http://www.ubuntuforums.org/showpost.php?p=1731224&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1731224&postcount=29)

---

