---
title: "nVidia Display Driver Works Until Reboot"
date: 2007-04-05
forum: General Help
---

### Post by CarlosinFL on 2007-04-05
So my ubuntu system has a problem. I can install the latest nvidia driver from nvidia.com fine. I kill "X" and then run the nvidia shell script to build the kernel module and when it's done, I then reload "X" and I have perfect graphics on my Ubuntu box. But...I reboot and then my machine loads in CLI mode only as it can no longer read the xorg.conf file with the "nvidia" driver but if I kill "X" and change "nvidia" to "vesa" and reload "X", it then works again.

Why is the Nvidia driver only working until I reboot my machine. This makes no sense to me.

---

### Post by spin2cool on 2007-04-06
My guess:  some necessary modules are loaded when you boot, then not removed when you restart the xserver after installing the new drivers.  So, they sit there working fine until the next boot, when they fail to load and things go to hell.

Have you tried using Envy to install the drivers?  
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It worked great for me, when I was having problems with the nvidia installer.

---

