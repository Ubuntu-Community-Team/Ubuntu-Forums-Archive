---
title: "Rolling Back LTS Kernels Due to AMD Issues"
date: 2016-03-13
forum: General Help
---

### Post by uRock on 2016-03-13
Hi all,

I had upgraded to the LTS Wily kernel and have noticed that graphics are messed up. When I open a movie via VLC the movie is jerky.

That said, I reinstalled the LTS Vivid kernel, but when I try to log in with it, it keeps going back to the log in screen.

Any thoughts on how I can get around this?

Output of **lspci** ```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
03:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe

```I'd be happy with getting the graphics to work properly in the current kernel or getting back into the Vivid kernel.
```
ubuntu@ubuntu:~$ uname -r
4.2.0-30-generic
```
Cheers & Beers,
uRock

Edit: Tried running ```
sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop
``` but that didn't do anything for the situation.

---

### Post by howefield on 2016-03-13
Uhm.. why remove nvidia - aren't you using an AMD card ?

---

### Post by grahammechanical on 2016-03-13
Have you tried any of the previous kernels list at the Grub menu under the Advanced options for Ubuntu sub-menu? As far as I know installing another kernel does not remove existing kernels. We either have to purge the kernel or use autoremove to do it. As far as I know.

Regards.

---

### Post by kansasnoob on 2016-03-14
Did you follow the steps here to get the Wily kernel and X-stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Trusty](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Trusty)

I wondered if possibly there is a mismatch between the kernel and X-stack currently in use.

---

### Post by uRock on 2016-03-14
> **howefield said:**
> Uhm.. why remove nvidia - aren't you using an AMD card ?

Probably why it didn't help. I was grasping at straws and saw a link mentioning that as a cure. 8)

---

### Post by uRock on 2016-03-14
> **grahammechanical said:**
> Have you tried any of the previous kernels list at the Grub menu under the Advanced options for Ubuntu sub-menu? As far as I know installing another kernel does not remove existing kernels. We either have to purge the kernel or use autoremove to do it. As far as I know.

Regards.
Using the old kernel is when I get stuck in the log in loop.
> **kansasnoob said:**
> Did you follow the steps here to get the Wily kernel and X-stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Trusty](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Trusty)

I wondered if possibly there is a mismatch between the kernel and X-stack currently in use.

I will look into that this evening. Thanks!

---

### Post by uRock on 2016-03-17
Just got around to running the install code listed. Came back with these errors. ```
dpkg: error processing archive /var/cache/apt/archives/xserver-xorg-core-lts-wily_2%3a1.17.2-1ubuntu9.1~trusty1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/xorg/modules/libglamoregl.so', which is also in package xserver-xorg-video-glamoregl 0.6.0-0ubuntu4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg-core-lts-wily_2%3a1.17.2-1ubuntu9.1~trusty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by uRock on 2016-03-18
After breaking some more things I decided to reinstall 14.04.1. 

Marked as solved.

Cheers & Beers,
uRock

---

### Post by uRock on 2016-03-19
I'm now back on the 3.19* kernel. Oddly enough, when I installed the AMD driver listed in Synaptic I ended up with the same choppy video. I found that unticking a box in VLC is all I had needed to do. That said, if anyone else is having this problem, then open VLC's preferences and go to the video section, then untick the **Accelerated video output (overlay)** option.
[ATTACH=CONFIG]267894[/ATTACH]

Cheers and Beers,
uRock

---

