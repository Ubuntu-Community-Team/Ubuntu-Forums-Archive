---
title: "Ubuntu 12.10 is working slow"
date: 2013-02-12
forum: General Help
---

### Post by srekcahrai on 2013-02-12
Hi, I have Ubuntu 12.10 installed in my PC and is laggy. These are my hardware, OS and software specifications:
Processor: Intel® Core™2 Duo CPU E4500 @ 2.20GHz × 2
RAM: 2.0 GiB
Graphics: Nvidia GeForce 7300 SE/7200 GS/PCIe/SSE2
OS: Ubuntu 12.10 32-bit
Display manager: GDM
Desktop environment: Gnome classic
Window manager: Compiz

The most laggy time is while using firefox. While typing the texts types laggy and hangs for few seconds. While scrolling I get two displays(same text typed together) It's also laggy while playing videos from youtube and vlc.

In compiz effects I have only Animations, Window Decoration and Wobbly Windows enabled. I don't want to disable compiz.

Please help and suggest me to make my Ubuntu work faster. Thank you.

---

### Post by dino99 on 2013-02-12
compiz needs too much ram/power on that hardware, you might not use it with heavy browser like firefox.

Either use chromium, which works great with flash, and/or login as gnome-classic (without effect)

---

### Post by ACubed10 on 2013-02-12
Also do are you using a proprietary graphics card driver?  Or are you using the graphics driver that came installed when you installed Ubuntu?

---

### Post by srekcahrai on 2013-02-12
> 
compiz needs too much ram/power on that hardware, you might not use it with heavy browser like firefox.

Either use chromium, which works great with flash, and/or login as gnome-classic (without effect)


Then I have no choice and have to leave compiz. What are the alternatives for compiz?

> 
Also do are you using a proprietary graphics card driver?  Or are you  using the graphics driver that came installed when you installed Ubuntu?


There were 5 options in  Additional Drivers
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-173 (proprietary)
- Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-current-updates (proprietary)
- Using Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-experimental-304 (proprietary)

I have choosen the first one:
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)

---

### Post by ACubed10 on 2013-02-12
> **srekcahrai said:**
> Then I have no choice and have to leave compiz. What are the alternatives for compiz?



There were 5 options in  Additional Drivers
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-173 (proprietary)
- Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-current-updates (proprietary)
- Using Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-experimental-304 (proprietary)

I have choosen the first one:
- Using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)
I have a GTX 550 Ti card, and the "Test" driver worked, but I got some bugs with opening, firefox typing things like that.  I install one of the newer drivers and I am flying right along.  Can even play game on steam with no video lag.  Maybe try that?

not saying this will be the solution for you, but it was for me

---

### Post by srekcahrai on 2013-02-12
> **ACubed10 said:**
> I have a GTX 550 Ti card, and the "Test" driver worked, but I got some bugs with opening, firefox typing things like that.  I install one of the newer drivers and I am flying right along.  Can even play game on steam with no video lag.  Maybe try that?

not saying this will be the solution for you, but it was for me
You mean the experimental one?

---

