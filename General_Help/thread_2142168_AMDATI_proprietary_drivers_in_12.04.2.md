---
title: "AMD/ATI proprietary drivers in 12.04.2"
date: 2013-05-04
forum: General Help
---

### Post by gifford on 2013-05-04
I did a fresh install of Ubuntu 12.04.2 and when I went to install the proprietary AMD/ATI drivers, I was given three choices:
ATI FGLRX  -post release update
ATI FGLRX  -experimental beta
Experimental AMD binary Xorg driver and kernel module

I installed first the post release update, but when I went to additional drivers it stated the driver is activated but not currently in use. 
However, when I used the terminal and entered fglrxinfo, it indicated the driver was in use.
Subsequently, I also installed the FGLRX experimental beta and got the same from additional drivers, driver is activated but not currently in use. It also says "No proprietary drivers are in use on this system."
 
Again, when I enter fglrxinfo it returns the following:
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI FirePro V4800 (FireGL) Graphics Adapter
OpenGL version string: 4.2.11978 Compatibility Profile Context FireGL

So, what is the problem with Additional Drivers indicating "No proprietary drivers are in use on this system." ?
Am I doing something wrong? What am I missing here?

---

