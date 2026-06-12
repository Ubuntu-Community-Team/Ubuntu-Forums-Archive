---
title: "Ubuntu 14.04 nvidia tesla drivers problems"
date: 2014-11-27
forum: General Help
---

### Post by jordi11 on 2014-11-27
Hi!
I'm trying to install the proprietary nvidia drivers for a NVIDIA tesla C2050 to make use of the openCL capabilities. I'm using an Ubuntu 14.04 and changed the kernel to 3.16 to get rid of an USB3 problem.

I installed the proprietary drivers using the GUI and also tried with the xorg-edgers packages but all give me the same result. When I reboot the system, after introducing the login credentials there is only at the screen the wallpaper and the mouse, with no performance issues such as the mouse moves slowly, etc.
I'm able to switch to a command line terminal and then purge the nvidia driver and after that reboot. Then, the nouveau driver is used and all is fine, but, as I need to use openCL, using this driver is not an option.

I already tried to install some drivers (always uninstalling the tested driver before installing a new one), from the recommended in the GUI before using the xorg-edgers packages, and the 340 version of the edgers and even the driver from the nvidia website.

 Any ideas on how to get a nvidia driver working in these settings?

Any help will be appreciated.

---

