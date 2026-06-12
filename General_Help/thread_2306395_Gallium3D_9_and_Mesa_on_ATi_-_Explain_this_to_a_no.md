---
title: "Gallium3D 9 and Mesa on ATi - Explain this to a noob"
date: 2015-12-15
forum: General Help
---

### Post by bellasnaru on 2015-12-15
Hey guys

ok basically ive done abit of reading on Gallium Drivers, and 99% of installation instructions and details i found seem heavily based on NVIDIA, but at the same time, gallium mixed with wine seems to double performance and improve running 3D Games such as tomb raider in wine 1.7

So i sort of understand it, but i was wondering if someone could explain to a newbie Gallium and kinda what it is, and if its available/easy to setup for ATi, and play games with. one thing ive noticed with winehq is alot of different games requiring alot of different "wine patch's" and compilations

Basically im just wondering if this software would work on a newer ATi 270 GPU or if its for older GPU's and if i should just stick with AMD Drivers

i wish i could just download a version of wine that just has everything haha. but i know thats pretty much dreaming

---

### Post by grahammechanical on 2015-12-15
There are proprietary video drivers and there are open source video drivers. The open source video driver is installed by default. We do not need to install it. When we install and tick the box labelled "Install third party software" a proprietary video driver is downloaded and installed as well as some proprietary video and audio codecs. The open source driver is not removed. It is only deactivated. 

 The open source video driver used with Nvidia graphic cards is called Nouveau. The open source video driver for ATI graphic cards is called Radeon. They both make use of the Mesa 3D graphics library which includes the Gallium 3D libraries.

I have an Nivida graphic adapter and when I am running on the open source video driver the System Settings>Details page will list Gallium as the graphics driver along with an Nvidia code name for the graphic adapter. When I am running on the Nvidia driver Details lists the commercial name of the graphic adapter. In my case it is GeForce GT220/PCIe/SSE2.

As I do not have an ATI video adapter I cannot say what the Detail pages will reveal for an ATI adapter.

Each new release of Ubuntu comes with the latest improvements to the open source video drivers as well as newer but stable proprietary video drivers. As a general rule, the newer the video hardware, the newer the video drivers required and that means a newer Ubuntu version.

As a general practice, the owners of proprietary video drivers will drop support for older video hardware from their latest video drivers. But that is not usually the case with the open source video drivers.

Are you still with me? Oh, there is a version of wine that has everything. It is called Windows.

[http://www.mesa3d.org/](http://www.mesa3d.org/)

[https://en.wikipedia.org/wiki/Gallium3D](https://en.wikipedia.org/wiki/Gallium3D)

Regards.

---

