---
title: "Nvidia driver"
date: 2007-04-04
forum: General Help
---

### Post by threegremlins on 2007-04-04
I used synaptic to get the drivers for my geforce 5500 card ran nvidia-glx-config enable and made sure nv was changed to nvidia and maybe it is the peculiarity of my box but it just couldn't find the nvidia  driver. on this site

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)


I followed the links to Nvidia and downloaded their Linux driver and installed it.
It said it was going to build a new kernal and it worked first time, no problems in the least. I don't know much about security but have I left an opening in my firewall? Will this nvidia built kernel conflict with the Ubuntu kernel? Should I be worried about other problems or is this so easy a solution that nobody wants to use it or tell anyone else about it?

---

### Post by phidia on 2007-04-04
I've done the same thing with my feisty install. Although in edgy (6.10) I was able to install through synaptic.
I don't know what security risk "hand" installing the nvidia driver is but it will cause problems when or if you want to upgrade kernel and video parts of your system.

---

### Post by irwa82 on 2007-04-05
Hi,

I think you will find that the manual nvidia install did not compile a new linux kernel but instead compiled a nvidia kernel module that loads with your current ubuntu linux kernel.

There should be no security risks to your current kernel by doing the nvidia driver install.

The only think to remember is that you must reinstall the nvidia driver every time you install a new kernel other wise you nvidia driver won't work and if you reboot the computer you may have problems loading into x (the graphical environment).

---

### Post by threegremlins on 2007-04-05
you maybe right, the part about building the kernel may have said rebuilding, it went so fast. it's somewhat of a relief it isn't a security issue. thanks for your responses. it's still snowing here and it was almost gone, we really need a few good days of rain to turn everything green.
Dave

---

### Post by phidia on 2007-04-05
Just a follow-up on this. Synaptic tells me that some parts of my system can't be upgraded, and the packages that are un-selected by synaptic all have to do with nvidia or the kernel.

---

### Post by threegremlins on 2007-04-05
I believe it, I tried installing a Linux CNC program and their website warned about issues with Nvidia and I ended up reinstalling everything. I've come across a few other programs that had the same warnings but the programs worked anyway. Next time it might be worth it to spend the extra bit and buy a better suited graphics card.
Dave

I always find new things after I post and it appears ATI/Nvidia are well advanced in 3d graphics drivers, there were a lot of other interesting bits of information like Apple going 3d but I read recently Ubuntu dropped the idea of going for a 3d interface. Check out this link

[http://kerneltrap.org/node/4033](http://kerneltrap.org/node/4033)

---

