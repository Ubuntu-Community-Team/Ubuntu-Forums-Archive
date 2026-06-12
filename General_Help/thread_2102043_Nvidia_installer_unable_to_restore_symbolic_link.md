---
title: "Nvidia installer unable to restore symbolic link"
date: 2013-01-06
forum: General Help
---

### Post by Marrea on 2013-01-06
Hi

I'm currently using Ubuntu 12.04 and yesterday updated to the 3.2.0-35 kernel, following which I reinstalled the proprietary driver for my FX 5200 card by running
```
sudo sh NIVIDIA-Linux-x86-173.14.35-pkg0.run
```  During reinstallation the nvidia installer gave a warning, which I have never come across before when using this installer:  *unable to restore symbolic link /usr/lib/i386-linux-gnu/mesa/libGL.so.1 - > libGL.so.1.2 (File exists)*.

Is the fact that the installer was unable to restore the symbolic link important?  And, if so, how do I go about fixing it?  I know that .so files are dynamically linked shared object library files but beyond that I am a little hazy!  For instance I am not sure whether *(File exists)* in the warning message means that the file libGL.so.1 exists or whether it means the file libGL.so.1.2 exists.

---

