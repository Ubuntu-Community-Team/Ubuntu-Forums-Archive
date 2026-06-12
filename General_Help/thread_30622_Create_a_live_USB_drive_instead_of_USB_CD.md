---
title: "Create a live USB drive instead of USB CD"
date: 2005-04-29
forum: General Help
---

### Post by divinerites on 2005-04-29
Hello,

I got a cheap external USB box and put an old 4 Go drive in it. All works fine.

With this cheap usb drive, I just want to create a **live USB drive** instead of a live CD beacuse it wouls have the advantage of :

[list]
[*]Boot from USB drive and act live a live CD
[*]Run **faster** from HD than from CD
[*]Use a HD partition and **save data** and configuration.
[/list] 

It seems impossible to find information on how to achieve that. I only can find information about install the distribution on the USB drive, but the drive is consequently tied to the PC hardware and it's not a live CD/USB drive .

Is it possible to achieve that ? 
And if yes, i would love to have some link, tip, pointer or any information about how to do that.

Thanks.

---

### Post by nad on 2005-04-29
I understand what you wish to do. The problem with any live distro is that the filesystems are hardware dependent; typically pen drive or cd, ram and possible non-persistent swap space on a physical drive. Support for all this needs to be included in the kernel and loaded early on as the os is loaded in stages from images. For the ultimate in live distro resources, see: [www.knoppix.org](www.knoppix.org) .

As far as an install being tied to pc hardware. Yes, the ubuntu x86 distro is tied to x86 hardware. I think what you mean is in the windoze sense in that a particular install includes specific drivers. An x86 kernel probes all hardware on startup and transparently installs necessary drivers from its' modules directory. Some necessary modules will need to be installed in the kernel, but any module built with the kernel is available. In this way, an install of ubuntu to your usb hard drive should boot any computer that is able to boot from a usb port.

---

### Post by nad on 2005-05-02
A follow up to my previous post.

I found a package in universe called bootcd. "Copy your running Debian System on CD with the command bootcdwrite".

This may just fill the bill.

---

