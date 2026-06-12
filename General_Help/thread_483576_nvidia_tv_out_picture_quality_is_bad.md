---
title: "nvidia tv out picture quality is bad"
date: 2007-06-24
forum: General Help
---

### Post by berock on 2007-06-24
Recently, I installed ubuntu server and installed fluxbox for a window manager (going to be a mythtv box so I just want a light window manager).  I've got my nvidia video card working properly in clone mode with a composite cable running into my TV. I'm having a problem with the picture quality on the tv out.  It is showing a very distorted/pixelated picture.  While the machine is booting before X starts, the quality is fine but as soon as X starts (and the nvidia drivers load ?), then the picture quality gets very bad.  Even if I then kill X and drop down to a terminal, the quality is bad. Bear in mind that I have used this composite cable before for TV out onto this TV without this problem so I know that the cable is fine.  

I'm wondering if there is an option that I need to set in my xorg.conf, if the nvidia drivers have some problem in ubuntu (grasping at straws) because I had this working without problem in my previous gentoo installation.

I've attached my xorg.conf.

Thanks for any ideas out there...

---

### Post by berock on 2007-06-24
I've also noticed this in my X log:

(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(WW) NVIDIA(1): Unable to load "xf86ExecX86int10".
(EE) NVIDIA(1): Unable to initialize the X Int10 module; the console may not
(EE) NVIDIA(1):     be restored correctly on your TV.

I cannot seem to find a fix for this issue yet .. ideas?

---

