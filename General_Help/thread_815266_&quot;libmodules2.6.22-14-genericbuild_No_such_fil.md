---
title: "&quot;/lib/modules/2.6.22-14-generic/build: No such file or directory&quot;"
date: 2008-06-01
forum: General Help
---

### Post by Joe88 on 2008-06-01
I'm trying to install pwc drivers for my mums Logitech QuickCam Pro 3000 web camera on her computer wich has Ubuntu 8.04.

I've unzipped the source and followed the instructions given in the install readme, when I do the make command, the terminal tells me the build folder in the "/lib/modules/2.6.22-14-generic" directory is missing.

The kernel Image for 2.6.22-14 was installed but not the source. I've installed the source for 2.6.22-14 (not using synaptic manager), but the build directory has not appeared and the error message still comes up.

Anyone know how I can solve this problem?

---

### Post by Joe88 on 2008-06-04
I've now installed the pcw drivers using the easypcw script from ubuntu 8.04's synpatic package manager. Its in french, but you just need to click ok and it will automatically install the drivers and not present any error messages if the drivers were installed successfully.

The problem I have now is that i don't know how to set the pwc driver for my mums webcam in /dev/video1 - I've tried using sudo setpwc -d /dev/video1 and its still set to my tv card in /dev/video0.

I also want to use the pcw driver in aMSN and when I run the webcame wizard I just get the v4l2 driver - theres no sign of the pcw driver, which I guess reflects the fact the driver has been set to my TV card and not my mums webcam.

Please help if you can.

---

