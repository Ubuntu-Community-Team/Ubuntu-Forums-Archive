---
title: "Two Displays on one Screen?"
date: 2008-01-16
forum: General Help
---

### Post by GoofusGreen on 2008-01-16
Hi everybody,

Recently I've been having some issues with my graphics in Ubuntu. I'm running ubuntu 7.10 and fglrx 8.443.1

Here's what happens:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.1.7170 Release

and then

$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

etc etc

and...

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)


There is one error in /var/log/Xorg.0.log 

(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2

---

### Post by pointone on 2008-01-16
Are you still running Xgl? It's not necessary with the latest ATI drivers, which support AIGLX.

---

### Post by GoofusGreen on 2008-01-16
Hey thanks!

That was the problem. I got rid of xserver-xgl and voila, problem gone. And my 3D games in linux work now too thanks to the new ATI Catalyst 7.12 driver. Yummy. Now all I need to do is get my computer to recognize my screen as a 1440x900 again. This 1280x720 is bugging me. (X seems to be ignoring my modelines in xorg.conf, not cool)

---

### Post by pointone on 2008-01-18
This is a known bug with the 7.12 release. 8.01 was just released, and solves this problem.

---

### Post by GoofusGreen on 2008-01-19
I've "upgraded" to Catalyst 8.1. glxgears skips every few seconds and has an fps of around 60 rather than the 5000fps i was getting before. UrbanTerror gets 60 fps instead of 90. All in all, nothing works better, and everything is worse.

One thing is fixed, actually. My screen res is back to normal! Wahoo!

---

### Post by pointone on 2008-01-19
Make sure the kernel module is being loaded properly. I recommend following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually").

---

