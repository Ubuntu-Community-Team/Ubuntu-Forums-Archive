---
title: "Compiz Fusion Help"
date: 2008-03-15
forum: General Help
---

### Post by LinuxNewb092 on 2008-03-15
Hey guys I just installed Compiz and I was wondering how you make Windows burn out when you "X" out of them.  I was also wondering how you make it so a cube appears showing the top, bottom, and all four sides.  Any help would be much appreciated.

---

### Post by freebios on 2008-03-15
go to snyptic hit search and search for l compiz-config or compiz config and install it.  then go to system - preferences - advanced desktop effects and enable desktop cube.  then restart you computer and to do the cube hold ctrl+alt and left mouse button will do the rotation, or just use the middle mouse button.  once you do that you can also enable fire from the same control pannel and you can also enable cube caps there too by checking those things.  let me know if you need more help.

---

### Post by sosipator on 2008-03-16
Hello guys, I'm also trying to enable fire on the windows, but somehow it doesn't work. I have that effect turned on, and the settings are okay but it doesn't make the windows disappear in flames. Maybe i have some other effect enabled that have to be unchecked. 
Any idea how to make it work?

---

### Post by Hazed on 2008-03-16
Are you sure you have enabled the Animations plugin? And set the Close Animation to Burn?

If so, make sure you have your graphics drivers installed (Nvidia, ATI) as Compiz requires 3D Acceleration I believe.

---

### Post by lilalmond on 2008-03-16
If you have changed the settings in advanced desktop effect settings and it doesnt seem to work, then open a terminal and type "compiz".
Thats what i did to activate the effects and it worked out  (i was trying to make the animations work like the magic lamp and domino...)

---

### Post by sosipator on 2008-03-16
Thanks guys,

I guess that would be the problem (the Nvidia drivers)

When i type compiz it gives me this:

sosipator@ubuntu:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

I have the drivers for Nvidia installed, even the restricted one. And I'm sure it supports 3D acceleration. I've seen somewhere a tool to manage graphic drivers envy or something, I'll try with that. There has to be a way to enable that effect.

---

