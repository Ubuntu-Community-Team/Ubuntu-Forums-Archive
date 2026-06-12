---
title: "nvidia confusion"
date: 2006-12-08
forum: General Help
---

### Post by gary101 on 2006-12-08
Hi
Having a few problems with NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]

I am using Dapper with the following shown as installed in synaptic

1) Non-free Linux 2.6.15 modules on 386  2.6.15.11 -4
2) Non-free Linux 2.6.15 modules on 386  2.6.15.12 -1
3) NVIDIA binary XFree86 4.x/X.Org 'legacy' driver  1.0.7174+2.6.15.12 -1
4) NVIDIA binary kernel module common files 20051028+1
5) smartdimmer 0.1-2
6) X.Org X server -- NV display driver 1:1.0.1.5-0ubuntu4

Only just installed number 3 rebooted and now when I start bzflag I get the following:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Could not set Video Mode: Couldn't find matching GLX visual.
Error creating window - Exiting

My question is this, should I uninstall number 6 (above)?
driver is showing as 'nv' should I change it to 'nvidia'?
Thanks

---

### Post by K.Mandla on 2006-12-10
Yes, you should change nv to nvidia in your xorg.conf file. Don't bother with the nv driver; it's installed by default, and the nvidia-glx (non-legacy) will probably give you errors.

Some of the older cards don't handle glx like the newer ones, even with the nvidia-glx-legacy driver. I had the same problem with a 64Mb Geforce2 Ti. By all accounts, that should be more than enough memory to handle Beryl and a mess of 3D games, but it wouldn't do the nvidia-glx driver, and with the legacy driver it gave me the same errors you have.

---

### Post by Azakus on 2006-12-10
I agree. The glx driver specifically does not support your card. Only the legacy does.

---

### Post by gary101 on 2006-12-10
Thanks Guys

Should I also get rid of 'load dri' in the xorgcof?

---

