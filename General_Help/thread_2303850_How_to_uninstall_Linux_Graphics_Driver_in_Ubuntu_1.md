---
title: "How to uninstall Linux Graphics Driver in Ubuntu 15.04?"
date: 2015-11-22
forum: General Help
---

### Post by jagandecapri on 2015-11-22
I have installed Linux Graphics Driver through the installer in [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.1)

However, I would prefer to use my Nvidia card instead. How do I uninstall the Linux Graphic Driver?

I have tried the guide in the following link without any success [http://theclonker.de/?p=89](http://theclonker.de/?p=89)

`lspci -vnn | grep -i VGA -A 12` still shows Intel Graphics Controller as the kernel driver in use.

Any idea on how to solve this?

Thanks.

---

### Post by grahammechanical on 2015-11-22
I am a little confused. According to that link you have not installed a Linux graphics driver but an Intel installer that installs the latest Intel graphics driver for Linux. 

> The Intel® Graphics Installer for Linux* allows you to easily install  the latest graphics and video drivers for your Intel graphics hardware.  This allows you to stay current with the latest enhancements,  optimizations, and fixes to the Intel® Graphics Stack to ensure the best  user experience with your Intel® graphics hardware. The Intel® Graphics  Installer for Linux* is available for the latest version of Ubuntu*.

If you have an on-board Intel graphic adapter and a discrete Nvidia graphic adapter then Additional Drivers will allow you to install a Nvidia proprietary video driver. It will come with an Nvidia Xserver settings utility and that may allow you to switch between Intel and Nvida graphic adapters.

Regards.

---

### Post by buzzingrobot on 2015-11-22
You don't need to uninstall the Intel driver.

If the Nvidia is disabled, i.e., turned off in the BIOS, it can't be detected.  If it is enabled, then Additional Drivers should find it and offer one or more drivers.

---

