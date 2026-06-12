---
title: "nVidia driver is very slow in 14.10 64bit"
date: 2015-04-19
forum: General Help
---

### Post by stepheny on 2015-04-19
I have an Ubuntu 14.04 32bit partition on my Packard Bell Easynote TS Laptop. I use Bumblebee to switch from the Intel GPU to the nVidia GeForce GT540M GPU when watching vidios etc, I have never had any problems with Bumblebee and its forerunner, Ironside and by running glxgears with optirun I get around 900FPS as opposed to 60FPS running glxgears using the Intel GPU

I have recently installed a 64bit 14.10 partition on the same laptop and tried to set up Bumblebee but have had problems. Running glxgears or glxspheres64 both run at 60FPS on both the Intel and nVidia GPU. At first I thought that Bumblebee wasn't actually switching the GPU but by running google-chrome in a terminal with and without optirun I can see that the GPU actually changes from the Intel to the nVidia. But there is no performance increase! I am using the proprietary driver nvidia-331.113 at the moment but have tried all of the drivers available in "system-software and updates-additional drivers" and have also tried nvidia-311 from xorg-edgers. This is the driver that works perfectly on the 14.04 32bit OS on exactly the same machine!

Does anyone have any ideas of what might be wrong?

---

### Post by stepheny on 2015-04-26
Apparently what is happening is that the FPS is being limited to the maximum refresh rate of the monitor, which is 60FPS on my laptop.

---

