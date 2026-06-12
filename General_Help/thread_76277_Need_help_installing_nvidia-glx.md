---
title: "Need help installing nvidia-glx"
date: 2005-10-14
forum: General Help
---

### Post by kudu on 2005-10-14
I tried installing nvidia-glx and it broke X. Worked fine in Hoary but Breezy doesn't like it. Please help! What's the correct procedure ? Thanks!

kudu

---

### Post by Qrk on 2005-10-14
Did you install the restricted modules package for your kernel?

---

### Post by kudu on 2005-10-14
Ahh! Yes...I think that's it. I'll do it and see what happens. Thanks!

kudu

---

### Post by kudu on 2005-10-15
Still not working. I'm getting the following error message when I try to run glxgears in a terminal:

~$glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


What the heck ??

---

### Post by kudu on 2005-10-15
I'm not getting the nvidia splash screen either.

---

### Post by rseymour on 2005-10-15
don't know which card you're trying to get working? i'm running a 6800gt and this is what seems to work for me:

using synaptic ... install nvidia-glx (the 7667 driver is the most current ubuntu pkg?) if you don't already have it installed.

then make a backup copy of xorg.conf in the /etc/X11 directory.

edit xorg.conf ... you want to comment out the glcore and dri lines (under the section "modules") ... make sure you have a load "glx"; change "nv" to nvidia (section "device"); and if necessary edit your monitor's HorizSync and VertRefresh parameters (section "monitor".

when that's done, I usually shut down.

hopefully on boot you'll be set.

run glxgears or glxgears -i iacknowlegethatthistoolisnotabenchmark (if you want your frame rates)

---

### Post by rdw200169 on 2005-10-15
after you install the nvidia-glx package you have to run:

#nvidia-glx-config enable

you have to do that before the video drivers will work.
the nvidia drivers are AWESOME!!!  after that, you should
be done, FOREVER.  3D Acceleration out of the box, beat that ATI.

---

