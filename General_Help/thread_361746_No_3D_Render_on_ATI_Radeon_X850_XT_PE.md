---
title: "No 3D Render on ATI Radeon X850 XT PE"
date: 2007-02-14
forum: General Help
---

### Post by h1voltage on 2007-02-14
Hi Everyone,
I am a total n00b and trying to get used to using Ubuntu.  I have completely abandoned M$ for good! :)

I have been having a number of problems getting direct 3D rendering to work using on my ATI Radeon X850 XT PE video card.  I am currently running with the fgrlx drivers with dual screens.  Ximera is enabled.  I can post my xorg.conf file if needed.

Output from fglrxinfo:
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I have gone through a number of tutorials on enabling direct rendering.  Any suggestions?

On the topic of things not working, when I try to log off after I have logged in for the first time since reboot, i get either completely blank screens (the LCDs have actually turned off) or artifacts with black lines on a mainly beige screen.  

 I cannot even turn off the computer without having to do a hard reset!  What could be causing that?

System specs;
Asus Crosshair Mobo
AMD64 X2 4600+
2GB DDR2
4x WD 250GB HD

Thanks!

---

### Post by dcstar on 2007-02-14
> **h1voltage said:**
> Hi Everyone,
I am a total n00b and trying to get used to using Ubuntu.  I have completely abandoned M$ for good! :)

I have been having a number of problems getting direct 3D rendering to work using on my ATI Radeon X850 XT PE video card.  I am currently running with the fgrlx drivers with dual screens.  Ximera is enabled.  I can post my xorg.conf file if needed.

Output from fglrxinfo:


I have gone through a number of tutorials on enabling direct rendering.  Any suggestions?

On the topic of things not working, when I try to log off after I have logged in for the first time since reboot, i get either completely blank screens (the LCDs have actually turned off) or artifacts with black lines on a mainly beige screen.  

 I cannot even turn off the computer without having to do a hard reset!  What could be causing that?

System specs;
Asus Crosshair Mobo
AMD64 X2 4600+
2GB DDR2
4x WD 250GB HD

Thanks!

Some people have been using the "Envy" script to automate ATI/Nvidia driver installation, you may want to search out the forum posts for the URL.

---

