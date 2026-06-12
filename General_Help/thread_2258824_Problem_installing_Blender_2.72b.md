---
title: "Problem installing Blender 2.72b"
date: 2014-12-30
forum: General Help
---

### Post by pieter512 on 2014-12-30
Hello

I recently did a new install of Ubuntu, and I'm having problems installing Blender 2.72b. I downloaded it from the official site, unpacked it, and created a desktop file. I've got the Nvidia graphics driver installed (version 331.113, for my geForce GT650M), but when I go to 'user preferences' in Blender, I don't have the option to render on GPU. I tried restarting my computer, and running several previous versions of Blender and the newest release candidate, but the only option I get is CPU. I've used Blender 2.70 on Ubuntu 14.04 before, without encountering any problems.
The second problem is that there seems to be something wrong with the .desktop file. I added it to the Ubuntu launcher, but when I click it, it creates a different, lower resolution blender icon in the launcher. Why is this? It worked on my previous Ubuntu system...

Screenshots can be found [here.]("http://1drv.ms/1Bh2yuJ")

Any help appreciated! 

Pieter

---

### Post by pieter512 on 2015-01-03
I tried installing the second Nvidia driver (also 331.113) in the additional drivers tab. It gave me [this]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1401355") error, but now CUDA is working properly. 
However the problem with the launcher persists, but I have the same problem on Windows 8.1. Maybe just an error in Blender 2.72b ...

---

