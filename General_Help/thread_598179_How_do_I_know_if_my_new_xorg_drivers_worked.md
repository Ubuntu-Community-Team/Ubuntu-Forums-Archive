---
title: "How do I know if my new xorg drivers worked?"
date: 2007-10-31
forum: General Help
---

### Post by thenetduck on 2007-10-31
sounds like a stupid question but I used this script

[http://ubuntuforums.org/showthread.php?p=3675824#post3675824](http://ubuntuforums.org/showthread.php?p=3675824#post3675824)

and I don't know if I am using the drivers yet. So far to crashes and I attribute them to falty versa drivers. 

The Net Duck

---

### Post by mikewhatever on 2007-10-31
Try the following

glxinfo

or

glxinfo | grep OpenGL

Here's what I get

> $ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 97.55


---

### Post by redhavoc on 2007-10-31
I believe what you are asking is, how do I know that I get 3D out of my drivers

the best way to check that, is by issuing the command

glxinfo | grep rendering

if you get the response

direct rendering: Yes

then you have 3D, if the answer is no then you need to change certain stuff in your xorg.conf. Usually running

sudo nvidia-config 

should set things straight, but you might need to change thing in your /etc/X11/xorg.conf manually.

---

### Post by thenetduck on 2007-10-31
Ok I did that command it it says that I have 3d but the desktop effects still don't work... 

I have S3 Unichrome Pro intergraded graphics card. 

Any solution? 

Also, I thought this would fix my problem with random programs crashing when I play media etc. but it hasn't. This is very agrivating because I hear so much about how Gusty is stable and I really like the new features but for my computer... it doesn't work very well. 

Any ideas? 

The Net Duck

---

