---
title: "glx extention not being recognized"
date: 2008-06-21
forum: General Help
---

### Post by 999alfred on 2008-06-21
I cannot seem to get the glsx extention to be recognized. Here is what glxinfo gives me
~$ glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
wd4nmq@misty:~$ less /var/lo
local/ lock/  log/   
wd4nmq@misty:~$ less /var/log/Xorg.0.log
wd4nmq@misty:~$ glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

But, /var/log/Xorg.0.log has:
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9639
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.1.1
        ABI class: X.Org Video Driver, version 1.1

It would seem the X is loading the extention. So, why would everything that wants to use it complain and glsinfo say it is missing?

tj

---

### Post by macaholic on 2008-06-21
What type of graphics card do you use?

---

### Post by 999alfred on 2008-06-21
A GeForce2 MX.
And, I actually do get an error message further down the log file.

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

tj

---

### Post by 999alfred on 2008-06-21
I just noticed something else. No where in the log file is GLcore mentioned, but in the xorg.conf I have:

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

And, on another system with a GeForce4 Glcore is started, according to the log file.

Is this a clue, and if so what does it mean? Because, the log file does not even mention an error loading GLcore.

tj

---

### Post by macaholic on 2008-06-21
Do you have the nvidia restricted driver enabled in System > Administration > Hardware Drivers?

---

### Post by Forlong on 2008-06-22
Post your **/etc/X11/xorg.conf** and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by 999alfred on 2008-06-22
Well, now I am totally screwed. I went to the restricted drivers menu and enabled the nvidia accelerated drivers. Now I can not get the resolution to any thing other then 800x600. In the System>Administration>Screen and Graphics I select nvidia GeForece2 integrated and LCD 1280x1024, my AOC LM942 is not listed. But, select OK and it does not change it stays the same 800x600 generic screen.
 
Hell, I go to restricted drivers to turn off the Nvidia drivers and there is no provision for doing that.

So, the hell with GLX, how do I get my graphics BACK TO THE WAY IT WAS??????

I thought Ubuntu was supposed to be the "do everything for you" distro?

tj

---

