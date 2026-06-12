---
title: "[SOLVED] Compiz Fusion not working"
date: 2008-04-27
forum: General Help
---

### Post by crash91 on 2008-04-27
Im running Hardy 64-bit on a Intel 945GM graphics card (Dell Inspiron 6400). 

When i try to start compiz:
```
crash@crash-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```
(also while trying to start compiz-fusion it tells me it failed to start display 0.0 (or something like that) and then metacity/xorg crashes.
 
and
```
crash@crash-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

When i try to check for the video driver:
```
crash@crash-laptop:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Im using 915Resolution to get my resolution to 1280*800, could this be the problem? 
Please help!

Crash

---

### Post by Glaxed on 2008-04-27
I've been where you are friend - and this fixed it all for me;

1. Open xorg.conf
$ gksudo gedit /etc/X11/xorg.conf

2. Scroll to Section "Screen"
3. Add 	Defaultdepth 24, Option "AddARGBGLXVisuals" "True", and Option "DisableGLXRootClipping" "True" under that section e.g (Dont copy this exactly.):
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Defaultdepth	24
#	Device		"Configured Video Device" 
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"	
	Option 		"AddARGBGLXVisuals" "True"
	Option 		"DisableGLXRootClipping" "True"
	
EndSection

```

also make sure that the correct driver is specified for Section "Device". e.g:
```

Section "Device"
	Identifier	"Configured Video Device"
#	Driver		"vesa" or w/e your driver is
	Driver		"i810"
EndSection

```
4. Close the file and open /usr/bin/compiz
$ gksudo gedit /usr/bin/compiz
5. Add intel and i810 to the whitelist. Install xserver-xorg-video-i810 for good measure.

There is some more hacking you can do with /usr/bin/compiz, but it's risky, so don't.
Now try launching Compiz in a terminal with;
$ SKIP_CHECKS=yes compiz

Good luck.

---

### Post by crash91 on 2008-04-28
Thanks! It worked, i just have one more problem, when i try to use the desktop cube...its not a cube - its only two sided. When i try to do 3 or more desktops, X crashes and i have to relogin.

---

### Post by Glaxed on 2008-04-28
Ouch. Report that.
But try this first -

$ ccsm
and go to general options --> desktop size --> and increase horizontal virtue to 4.
Then go to display settings and select the 'Best' texture filter and put overlapping output handling in smart mode.

---

### Post by crash91 on 2008-04-29
I tried that, but it seems to be caused by the 3D windows plugin. I can live without that though :)

---

