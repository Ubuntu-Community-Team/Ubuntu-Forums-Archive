---
title: "[SOLVED] Garbled screen in vesa"
date: 2008-01-27
forum: General Help
---

### Post by Toadmund on 2008-01-27
I needed to resort to the vesa driver due to a black screen issue arising from a need to try and change an unadjustable refresh rate.
Anyway, the vesa driver got me out of the black screen after login, problem now, the screen after login is all garbled at a slant.
I know this must have something to do with a resolution setting or a refresh rate, but I am at a loss to fix the problem, I am only able to use the terminal.
I do notice that in xorg.conf there is no part about horizontal and vertical refresh rates under 

section "monitor"

???
I tried reducing the vertical refresh rate in 
```
sudo dpkg-reconfigure xserver-xorg
```
that didn't work.

I am really stuck here, and need a pointer in the right direction.
Thanks.

---

### Post by Ub1476 on 2008-01-27
The VESA driver is just a fails-safe driver, so it's not meant to be used for normal computing:)

Are you sure you installed the correct drivers for your graphic card before fiddling with xorg.conf?

---

### Post by Toadmund on 2008-01-27
I _am_ using the vesa as a failsafe as I cannot use my ATI driver.

Using the vesa allows me to not have the black screen after login.

---

### Post by Toadmund on 2008-01-27
OK, I fixed it, I simply deleted the higher resolutions or 'Modes' from xorg.conf, which left me this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes	   "800x600" "640x480"
```

The higher resolutions appeared to be the problem, now to re-install my ATI driver.

---

### Post by Toadmund on 2008-01-27
OK, I fixed it, I simply deleted the higher resolutions or 'Modes' from xorg.conf, which left me this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes	   "800x600" "640x480"
```

The higher resolutions appeared to be the problem, now to re-install my ATI driver.

---

