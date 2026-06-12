---
title: "Intel/AMD open source drivers"
date: 2014-07-14
forum: General Help
---

### Post by riko442 on 2014-07-14
Okey, so I've got hybrid graphic card Intel/AMD and so far I haven't much problems with proprietary drivers, even if performance is questionable and it looked like no fglrx is in use, but I would like to use open source drivers. After installation of Ubuntu 14.10 driver manager looks like this.
[IMG]http://i.imgur.com/FOsboMj.png[/IMG]

... which means that I am using Open source ATI driver, at least according to driver manager.

But when I run 
lspci -nnk | grep -i vga -A3 | grep 'in use'

I got Kernel driver in use: i915 which means that I am not using Radeon driver, but Intel driver.

When I Do lspci -nnk | grep -i vga -A3

I got
 00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0156] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:1972]
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)

When I look through synaptic, it say that I've video ati installed and also video-intel. This all was by default.

So how to use radeon driver and not intel one? Is there possibility of switching between them or, why does driver manager says I am using ati driver when terminal says no?

---

### Post by grahammechanical on 2014-07-14
My guess and it is not based upon any experience is that the system is showing that it is using the Intel driver because the system is running on the Intel graphics adapter. If the system was running on the AMD adapter then the system would be using the driver indicated by Additional Drivers utility. You have two graphic adapters, so you need a driver for each of them.

These links you may find useful. You may need to install this amd-indicator to switch between the two cards.

[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)

[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

The answer covers versions of Ubuntu up to 13.10. It has not been improved to cover 14.04.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards.

---

