---
title: "Problems using Nvidia accelerated graphics drivers: mouse and keyboard lag"
date: 2014-03-02
forum: General Help
---

### Post by darcy2 on 2014-03-02
Hi All, 


A few days ago I installed Ubuntu 12.04 on my Macbook Pro (mid-2009, 5,5). My problem is that I can't install the Nvidia accelerated graphics driver without my touchpad and keyboard becoming extremely laggy to the point where they are unusable. It's fine for about 5-10 minutes after boot up and then it seems as if at random the mouse and keyboard will suddenly become really unresponsive and slow. They'll stay that way until I reboot and then the same thing happens again after several minutes. The computer otherwise runs at normal speed. I can watch videos, for example. I just can't type or use the mouse cursor without them being really laggy. 


I've tried the recommended Nvidia driver in the Additional Drivers menu, as well as several of the other Nvidia drivers listed, all have the same problem. When I remove the driver and revert to the generic nouveau driver, the problem disappears, however this creates problems of its own: scrambled splash screen, system freeze on suspend, etc. 


Has anyone else encountered this problem or does anyone know a solution to it? 


Sincerely,
 D


System specs: 


Ubuntu release 12.04 64-bit
Kernel Linux 3.11.0-17-generic
GNOME 3.4.2


Graphics card: Nvidia GeForce 9400M ver.b1


Memory: 7.5 GB
Processor: intel core 2 duo 2.26GHz x 2

---

### Post by Broshea on 2014-03-31
I am having a similar problem, where the mouse, keyboard, and window manager occasionally become very unresponsive and slow after I upgraded the kernel from 3.2.0-59-generic to 3.11.0-18-generic, and upgraded the NVIDIA GeForce driver from 304 to version 331, using the Additional Drivers utility.

The slowness usually happens when I am building a large project from source code, which at first doesn't seem out of the ordinary, but this has become much worse since I upgraded the kernel and NVIDIA graphics driver, to the point of being unusable for periods of a few minutes at a time.

Ubuntu release: 12.04 64-bit
Kernel version: 3.11.0-18-generic
Graphics card: NVIDIA GeForce Quadro 600
GNOME 3.4.1.1
Processor: Intel Xeon CPU E5-1660 0 @ 3.30GHz x 12
Memory: 32 GB

I'm not sure about the specific revision of the graphics card, as it is a work system and I didn't purchase the parts myself.  Here is the output of "lspci -nnk" for the NVIDIA graphics device, which appears to show that it is revision a1 (decimal 161), if that is relevant:

```

03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GL [Quadro 600] [10de:0df8] (rev a1)
        Subsystem: NVIDIA Corporation Device [10de:0835]
        Kernel driver in use: nvidia
        Kernel modules: nvidia_304, nvidia_331, nouveau, nvidiafb

```

Is it possible that there is an issue with the fact that the list of kernel modules includes the previous version of the NVIDIA driver (nvidia_304), as well as the new one that I upgraded to (nvidia_331)?  Do I need to remove this previous version?

Thanks.

---

### Post by devin6 on 2014-04-18
Hello,

Same situation and problem as Darcy2. Any help would be appreciated. If it is a Kernel update thing, is there anyway to lock it into a precious stable version until the issue has been addressed? Which version is stable?

Thanks,
Devin

---

### Post by devin6 on 2014-05-08
Hello,

For what it is worth, I tried different scenarios and discovered that:

1) With the "Recommended" (331) NVidia drivers installed, I could not use the trackpad
2) I have evidence that it is confined to the trackpad because I used a USB mouse and everything works fine.
3) I have evidence that it has something to with the way the NVidia driver interacts with the trackpad because when I remove the NVidia driver and just use "Nouveau" everything works just fine.

For what it is worth, one can gather from this that a possible solution is to not install the NVidia driver when one is using Ubuntu 12.04 on a MacBook-Intel 5,5, and when one wants to use the trackpad.

If there are any better solutions, however, I am all ears.

Best,
Devin

---

