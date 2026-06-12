---
title: "Compiz anamation are missng after ubuntu upgrade"
date: 2008-06-11
forum: General Help
---

### Post by dondolo on 2008-06-11
hi guys i'm italian, my name is andrea. some days ago i run an upgrade, moving from 7.10 to 8.04. the problem is this: 

ALL THE EFFECTS ARE MISSING. emerald was too, but installing compiz-fusion-icon works fine right now. that is what my terminal returns after luanching compiz
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (colorfilter) - Info: Loading filter negative (item negative).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter negative-green (item negative-green).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter blueish-filter (item blueish-filter).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter sepia (item sepia).
/usr/bin/compiz.real (colorfilter) - Info: Loading filter grayscale (item grayscale).
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Close event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.


the same error over and over and over til when i close terminal.
3d effect doesn't work too, cube instead yes. 

if you are able to, please help me :)

---

### Post by nickdbliss on 2008-06-11
just want to know if u are having graphic adapter driver installed. What does this command shows? #glxinfo | grep rendering.

---

### Post by nickdbliss on 2008-06-11
also what does these commands show?

#glxinfo | grep vendor 

and

#fglrxinfo

---

### Post by dondolo on 2008-06-11
i got 3d acceleration. all the other effects are working properly. 
drivers are working fine

---

### Post by Kevbert on 2008-06-11
Try running [Compiz-check]("http://forlong.blogage.de/article/pages/Compiz-Check").  It may be the graphics driver has been blacklisted.

---

### Post by dondolo on 2008-06-11
it's impossible i got nvidia 8800gts 320 mb.....

---

### Post by Uchiha_madara on 2008-06-12
Install Compiz Fusion After Update Not Before it.:guitar::lolflag:

---

### Post by Forlong on 2008-06-12
Seems like a setup issue to me.

Did you install any third party Compiz packages on Gutsy?

---

### Post by Victormd on 2008-06-12
I ran into a similar problem when I upgraded so I ended up doing a fresh install and everything worked fine after that...

---

### Post by nickdbliss on 2008-06-13
Solved the same problem on my friends pc. Just reinstall compiz again.thanks

---

### Post by dondolo on 2008-06-18
> **Forlong said:**
> Seems like a setup issue to me.

Did you install any third party Compiz packages on Gutsy?

no i didn't, just uninstalling right now, i'll tell you if it works


did'nt work

---

### Post by Forlong on 2008-06-18
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

