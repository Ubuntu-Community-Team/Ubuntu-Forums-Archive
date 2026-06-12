---
title: "Update to kernel 3.8.0-21 from -19 stops X from starting on Dell XPS 12"
date: 2013-05-22
forum: General Help
---

### Post by palgorithm on 2013-05-22
It's basically all in the title. 

I'm on 64-bit 13.04, fairly fresh install, and in general the screen is black when you boot so you have to boost the brightness (it seems to default to 0 brightness), but since taking a minor kernel upgrade X will no longer start. I can swap to a terminal on control-shift-F1 for example, but there's nothing on F7. If I boot into 3.8.0-19, which I just happen to have installed, then everything is back to normal.

If you do login via the terminal, and look at the logs it appears to have failed to find a screen? I'm no expert here, so can only guess it's a regression of some sort. I assume I should report this as a bug somewhere but have no idea where.

Anyone have any suggestions?

Cheers,
Sam



[   237.041] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   237.042] (II) Module fbdevhw: vendor="X.Org Foundation"
[   237.042] 	compiled for 1.13.3, module version = 0.0.2
[   237.042] 	ABI class: X.Org Video Driver, version 13.1
[   237.042] (EE) intel(0): [drm] failed to set drm interface version: Permission denied [13].
[   237.042] (EE) intel(0): Failed to become DRM master.
[   237.042] (II) UnloadModule: "intel"
[   237.042] (EE) Screen(s) found, but none have a usable configuration.
[   237.042] 
Fatal server error:
[   237.042] no screens found
[   237.042] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   237.042] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   237.042] (EE) 
[   237.079] Server terminated with error (1). Closing log file.

---

### Post by mörgæs on 2013-05-24
Moved to General Help as this does not seem to be specific to Dell hardware.

---

