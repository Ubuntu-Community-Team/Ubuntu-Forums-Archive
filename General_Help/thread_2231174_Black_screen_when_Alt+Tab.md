---
title: "Black screen when Alt+Tab"
date: 2014-06-23
forum: General Help
---

### Post by waffen on 2014-06-23
Hello,
I obtain a black screen for some window software when I activate it, so I open for example Thunderbird, firefox and other one,if I minimize TB and after some time I use alt+tab to bring back to the front (the same with others shortcuts) I obtain a black screen please check my screenshot.

This behavior is the same for other software. 

I have a Lenovo ideapad S410p with NVIDIA Geforce

---

### Post by cincibluer6 on 2014-06-24
My guess is graphics driver off the top of my head. What version of Ubuntu are you running and what graphics driver?

---

### Post by waffen on 2014-06-24
I install the Nvidia driver I founded like the correct one for my card(I think) Heres the info:

Ubuntu 14.04 64 bits uptodate

mario@mario-IdeaPad-S410p:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 720M/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.79

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

mario@mario-IdeaPad-S410p:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)

---

### Post by waffen on 2014-06-27
Just for the records: this problem was fixed after I make a clean install for Ubuntu, I try everythig and not sucess, only reinstall and install all from ubuntu (not PPAs) make the fix

---

