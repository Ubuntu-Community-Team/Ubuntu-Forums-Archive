---
title: "WARNING: latest restricted-modules update will remove NVIDIA drivers"
date: 2007-03-02
forum: General Help
---

### Post by booe on 2007-03-02
This is a warning to anyone using the proprietary NVIDIA drivers (I have the latest ones installed, using NVIDIA's official installer off their website). I am using the x64 version of Ubuntu Edgy, fully updated from the repos.

The latest restricted modules update (from ~March 2nd) will remove the NVIDIA driver from the system, preventing your X server from booting up as per usual. You will then be thrown back to a prompt where you should do the following commands:

**NOTE before attempting any of the commands listed below:**
When you use the NVIDIA installation wizard, make sure that you:
1) Do NOT say 'yes' to finding a kernel module online. Instead, let the installer recompile a new kernel module. I assume that you have done this before when first installing the NVIDIA driver, and still have the build environment and required build packages installed.
2) Do NOT say 'yes' to reconfiguring your x.org config file - otherwise your settings and config will be overwritten, possibly causing you a few problems!

64bit version:
> 
bash
wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9746/NVIDIA-Linux-x86_64-1.0-9746-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9746/NVIDIA-Linux-x86_64-1.0-9746-pkg2.run)
sudo sh NVIDIA-Linux-x86_64-1.0-9746-pkg2.run
sudo reboot


32bit version:
> 
bash
wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run)
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo reboot


It should reboot, and the linux-restricted-modules package should be installed... and your display should be working properly with the recompiled NVIDIA kernel module.

---

### Post by frodon on 2007-03-02
It's not the latest but all the kernel update, when you install nvidia drivers outside the repositories then you have to install them each time you update your kernel.
Using the nvidia installer remove the restricted-module package which can be annoying for those who use specific wireless cards for example so if you install this packages of course it remove your custom nvidia driver install ;)

---

### Post by booe on 2007-03-02
> **frodon said:**
> It's not the latest but all the kernel update, when you install nvidia drivers outside the repositories then you have to install them each time you update your kernel.
Using the nvidia installer remove the restricted-module package which can be annoying for those who use specific wireless cards for example so if you install this packages of course it remove your custom nvidia driver install ;)

Thanks and yes, I use madwifi... which is why I have the restricted-module package installed.

---

### Post by mixium on 2007-03-02
Hi,

This is my first post here in Ubuntu forums. I am by no means a Linux noob but I am only a three day Ubuntu user so I have some questions directly relevant to this post. First a short story. Two days ago I installed Ubuntu-6.10-x86_64 on my new Core 2 Duo laptop because I have heard good things about Ubuntu and I really wanted to replace Vista 32bit with something that really supported 64 bit, especially with Linux. Upon installing Ubuntu I was greeted with a notice that 135 updates were available. Naturally I updated everything since quite a few were marked "Security Update" including the kernel.

My next step was installing nVidia 3D driver for my nVidia Geforce Go 7400. With the updated kernel there were no applicable prebuilt nVidia driver to match this kernel via apt. Browsing around in the forum I noticed a post pointing to Ubuntu prebuilt nVidia drivers in testing available via apt so I edited the apt source file and installed the prebuilt driver that matched my kernel. Upon reboot I was unable to get X back up and so I manually edited xorg.conf to switch to the driver "nv". X was back up, but the quality was not great. I create digital artwork for website customers as well as play 3D FPS's so have the 3D driver is critical to me.

Not having understanding for Ubuntu's methodology I took the easy way out and reinstalled Ubuntu. This time I have installed the nVidia 3D driver and none of the updates. Everything works, but I want to update at minimum the Security effected updates. Therein lies my problem...I don;t want to lose my driver to a updated kernel where an complimentary nNidia driver is not available. I also prefer to use Ubuntu's prebuilt module as opposed to the driver straight from nVidia while I am still trying to learn the "ins and outs" of a new Distro.

Sorry the story was so long...and here are my questions:

1. I can understand that security can have precedence over functionality. In this case updating the kernel has priority over a 3rd party's binary driver. But it amazes me that with the great amount of work involved with Ubuntu's dependency tracking I was able to hose my system without any warning from the package manager. Is this normal?

2. Before I update the kernel, knowing well in advance that there is no Ubuntu prebuilt 3D driver module, can I expect to be warned about the kernel breaking the driver? Remember, I am using the nVidia driver from Ubuntu's repo and not directly from the nVidia website. The reason I have to ask this is because the Ubuntu Linux kernel seems to be broken into multiple packages so I'm not sure how to proceed. Maybe it's not and I didn't look close enough.

What I am getting at is this. Can I be confident that if I update my system, the package manager will stop me or at the least warn me before updating the kernel and break X?

Again, I'm a 3 day old Ubuntu-Convert from the Slackware family of branches so please bear with me.

:)

Mixium

---

### Post by booe on 2007-03-04
mixium, this issue is being addressed in the next Ubuntu release. See [this](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x) specification for full details.

---

### Post by mixium on 2007-03-05
> **booe said:**
> mixium, this issue is being addressed in the next Ubuntu release. See [this](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x) specification for full details.

Thank you very much for that information. I must say that I am loving Ubuntu these days.

:KS

---

### Post by onuca on 2007-03-08
Hey Guys!

HELP! I did all as you have said and I am still having the problem! I am stuck in the text mode, please help!

---

