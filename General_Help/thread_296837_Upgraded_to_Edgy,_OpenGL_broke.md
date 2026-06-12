---
title: "Upgraded to Edgy, OpenGL broke"
date: 2006-11-10
forum: General Help
---

### Post by fictive-zeitgeist on 2006-11-10
Hey everyone...Ever since I updated to edgy(32bit), things have been runnin' kinda funky. 
This was to be expected, and I have managed to sort most of the stuff out,  my major problem is OpenGL.

I'm using an Nvidia Geforce 3 (I know, it's old, but it works for what I do)
I have updated my Nvidia driver as well(Version 1.0-9629).
Whenever I try to do ANYTHING involving OpenGL I just get a segfault.
This even happens when I try to access the OpenGL settings in the Nvidia X Server Settings tool.

If anyone has any information as to why this happens or how to resolve it, I'd be very greatful.

Example of my problem:
# glxinfo
name of display: :0.0
Segmentation fault (core dumped)

# glxgears
Segmentation fault (core dumped)

---

### Post by rogier.de.groot on 2006-11-10
I too ran into an OpenGL issue with Edgy. I fixed it by adding the line "Option "AllowGLXWithComposite" "True"" to my xorg.conf. But I'm not exactly sure this would fix your problem.
EDIT: I did this after looking at the xorg log file, and noticing it wouldn't load GLX because composite was enabled.

---

### Post by jsteve54302 on 2006-11-15
A note: 

 Rogier:
You're fix does allow X to start, but under Edgy the OpenGL extensions still do not load.  

Everyone:
To accomplish this, you must add the following to the end of /etc/X11/xorg.cof

Section "Extensions"
    Option "Composite" "0"
EndSection

Actually, I did both, but that's redundant - it doesn't matter if you allow glx/composite together, if you don't allow composite at all.

From the threads I've copied this from, it appears that Edgy uses something called composite drawing (i think) by default, which is not compatible with the fglrx drivers, and allowing fglrx and composite together just seems to disable the fglrx extensions (which just leaves you where you started - a laggy 2d display and no gl...)


Hope this helps,

---

