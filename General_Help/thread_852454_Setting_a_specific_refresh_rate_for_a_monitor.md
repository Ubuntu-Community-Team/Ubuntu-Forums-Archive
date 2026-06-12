---
title: "Setting a specific refresh rate for a monitor"
date: 2008-07-07
forum: General Help
---

### Post by Hopworks on 2008-07-07
I have an older, yet beautiful Viewsonic 15" monitor (CRT) that I want to use for my Ubuntu Gutsy Lamp server, but I'm having a real problem with the refresh rate. The monitor makes a high-pitched 'whistle' when the refresh is above 72hz vertical refresh at 1152x864. I tried to narrow the refresh rate options in xorg.conf, but when I get to gnome, and try to change the refresh rate in the screen resolution settings, it SAYS 50-something hz, but it's NOT because there is no flicker, and the monitor is whistling big time!

I just want to safely set it at 1152x864, 72hz refresh, and make that permanent.

Any ideas?

Thank you for your time!

Hop

---

### Post by mc4man on 2008-07-07
I've never used the server version so this may be a waste, anyway...
what I always found that worked in 7.10 with a nvidia card in getting an accurate range of refresh rate choices was first being fortunate in finding my monitors in _screens and graphics and setting it there_. That provides a good xorg with modelines ect. Then after a restart adding the line below marked with red arrow to xorg.conf allowed proper refresh rate choices. (shows some above and below as frame of reference), (may only be effective with restricted drivers? (nvidia), have never used the open source (nv))
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce 7800 Gs"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
        Option    "DynamicTwinView" "False"   [COLOR="Red"]<-[/COLOR]
        Option		"AddARGBVisuals"	"True"
        Option		"AddARGBGLXVisuals"	"True"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Dell P991"
	Vendorname	"Dell"
	Modelname	"Dell P991"
	Horizsync	30.0-107.0
	Vertrefresh	48.0-120.0
```
A couple of times setting up for others when the monitor wasn't listed I found listed models with same specs (from manufacturer's site or created modelines based on specs with online tool.
Edit : once I've gotten a good working xorg I've found it best to make a copy as a backup, future use, ect.

---

### Post by wolfen69 on 2008-07-07
```
gksu displayconfig-gtk
```

---

