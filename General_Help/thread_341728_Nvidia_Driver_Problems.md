---
title: "Nvidia Driver Problems"
date: 2007-01-19
forum: General Help
---

### Post by danakatheone on 2007-01-19
Alright, I messed up my Nvidia drivers. Whenever I try to use the nvidia drivers xserver doesnt start and i get the fatal error that it can't find "/lib/modules/(mygenerickernel)/volatile/nvidia.ko" (file doesn't exist how do i get it there?) and the error "wfb" module is missing. Then when I change xorg.conf to use "nv" it starts fine, but I can't do anything in 3d. Help?

---

### Post by Shatrat on 2007-01-19
Have you tried reinstalling the nvidia drivers?  
If you install them using nvidia's installer then you have to reinstall if you upgrade the kernel.

---

### Post by danakatheone on 2007-01-19
Yea, I reinstalled them from apt-get nvidia-glx and i get the same problem.

---

### Post by danakatheone on 2007-01-19
OK, I've messed with a few things and now I get when trying to start up xserv the error is "Failed to load module "wfb" (module does not exist, 0)" and the FATAL error is "Error running install command for nvidia"... improvement? I hope so....

---

### Post by bodhi.zazen on 2007-01-19
This is the easiest way to install/maintain the nvidia drivers:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by danakatheone on 2007-01-20
yay I fixed it by using that app to uninstall the drivers completely then did ```
sudo apt-get install nvidia-glx nvidia-kernel-common
``` then configuring the xorg.conf. Thanks.

---

