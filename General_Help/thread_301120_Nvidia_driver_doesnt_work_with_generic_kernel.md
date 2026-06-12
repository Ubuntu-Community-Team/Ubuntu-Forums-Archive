---
title: "Nvidia driver doesnt work with generic kernel"
date: 2006-11-16
forum: General Help
---

### Post by robgig1088 on 2006-11-16
Hey guys, I upgraded to edgy a few weeks ago and ever since the upgrade, I havent been able to load X with the generic kernel.  I'm no guru with kernels and X and such so I was wondering if anyone could help me get it up and running.  btw, the output from my /var/log/Xorg.0.log is:

..
...
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "crt, crt"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

:confused: 

thanks :D

---

### Post by Paul41 on 2006-11-17
Do you have the linux-restriced-modules installed for the generic kernel?

---

### Post by MJN on 2006-11-17
Given you appear to be using the proprietory driver ('nvidia') as apposed to 'nv' it's likely (if not an absolute necessity) to resinstall the nvidia driver now that you've upgraded your kernel.
 
Check out one of tseliot's many excellent guides on the topic at [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy).
 
In the meantime, if you change the 'driver' line in xorg.conf to 'nv' (not 'nvidia') then you may find X will run fine.
 
Mathew

---

