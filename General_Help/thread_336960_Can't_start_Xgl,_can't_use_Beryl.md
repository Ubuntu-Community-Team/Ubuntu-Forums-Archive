---
title: "Can't start Xgl, can't use Beryl"
date: 2007-01-12
forum: General Help
---

### Post by vd853 on 2007-01-12
I was installing Xgl and Beryl, but I'm getting that error when trying to enter Xgl. I've must have tried hours of updating, and reviewing the tutorial. ](*,) 

Currently using a Dell Inspiron 9300.  

I'm doing this on Ubuntu 6.10

FYI, I'm new to the whole Linux thing, and was trying to follow this tutorial:

[http://ubuntuexperiences.wordpress.com/2006/12/05/installing-beryl-and-xgl/](http://ubuntuexperiences.wordpress.com/2006/12/05/installing-beryl-and-xgl/)

Any ideas?

---

### Post by Sqwishy on 2007-01-12
Well beryl is relativly easy when you're using nvidia. Can you tell us if you're using nvidia or ati or intel!
Also try to follow the guides on these forums, they're usualy more up-to-date!
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by vd853 on 2007-01-12
nVidia Geforce 6800 GO

---

### Post by vd853 on 2007-01-12
> **Sqwishy said:**
> Well beryl is relativly easy when you're using nvidia. Can you tell us if you're using nvidia or ati or intel!
Also try to follow the guides on these forums, they're usualy more up-to-date!
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

I did a complete removal of XGL, and did that tutorial. I don't have a funny messed up purple screen, BUT I'm getting that. Some parts are frozen on screen, and other parts are moving awkwardly. I'm on the default session.

---

### Post by madrano on 2007-01-12
try this 

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

also, I was owner that blog (uexp), and completely up-to date

---

### Post by DirtDawg on 2007-01-12
Before you install AIGLX, you may need to "uninstall" GLX. If you're a gamer, this could cause problems. I'm not sure on this, but you may want to look into it.

The real reason I'm writing, however, is to let you know there's a screen-shot function under Applications>Accessories>Take Screenshot. It will probably be lots easier than using a camera. :D

---

### Post by ~LoKe on 2007-01-12
Yep, would definitely want to remove xgl before install AIGLX.
```
sudo dpkg -r xserver-xgl
```

---

### Post by vd853 on 2007-01-12
> **madrano said:**
> try this 

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

also, I was owner that blog (uexp), and completely up-to date

Xgl is uninstalled, and I followed that tutorial. Although I get the splash screen, I'm still getting the same problem with that black box, and part of the screen is frozen or messed up.

---

### Post by DirtDawg on 2007-01-12
Please post the error messages you receive from the terminal when running Beryl. Those may help clear things up a little.

---

### Post by vd853 on 2007-01-13
> **DirtDawg said:**
> Please post the error messages you receive from the terminal when running Beryl. Those may help clear things up a little.

This is what I get, then the splash screen follow by the messed up screen.

vdddd@vdddd-laptop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

** (process:5334): WARNING **: get_setting_is_integrated not found in backend ini

** (process:5334): WARNING **: get_setting_is_read_only not found in backend ini

** (process:5334): WARNING **: get_setting_is_integrated not found in backend ini

** (process:5334): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
Reloading all options.
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed
Framebuffer attach failed

---

### Post by cmost on 2007-01-13
Just jumping in here, but are you using the newest nvidia driver?  9631?  If not, install it using the 'Envy' script.  Then, you should be able to run Beryl without XGL or AIGLX using just the newest nvidia driver.  I know you're at your wits end with tutorials, but, some basic instructions are here:  Just make sure the following elements are present in the designated sections.  Leave the rest of your file as it already is.

$sudo gedit /etc/X11/xorg.conf

Section "Module"
[...]
Load "glx"
#Load "dri"   <--comment this out!
[...]
EndSection

[...]

Section "Device"
     Driver "nvidia"
     [...]
     Option "TripleBuffer" "True"
EndSection

Section "Screen"
     [...]
     Option "AddARGBGLXVisuals"
EndSection

Section "Extensions"
     Option "Composite" "Enable"
EndSection

Restart and hopefully you'll be enjoying some Beryl goodness.

---

### Post by vd853 on 2007-01-13
Ok guys we're almost there. I have it running, got the cube spinning too :), BUT there is NO title bar!! :confused:

---

### Post by vd853 on 2007-01-13
Oh never mind. I had to change the Defaultdepth. This site helped me figured it out - [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)

Thanks for all your help guys!!!

---

