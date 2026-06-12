---
title: "Dell Latitude 5420 i7-1185G7 problem with installation"
date: 2021-08-16
forum: General Help
---

### Post by ttmdear on 2021-08-16
[COLOR=#333333][FONT=Calibri]Hi,[/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri]A few days ago I bought a Dell Latitude 5420 i7-1185G7 Iris Xe Graphics. I have a problem with Udundu desktop installation. [/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri]Firstly I tried to install version 21.04. I prepared bootable USB storage with etcher. I plugged the USB, then ran the PC, pressed F12 and changed boot to boot from USB storage. The GRUB showed up quite quickly and then I selected to run Ubuntu. The process of starting the system is quite long but finally the ubuntu properly started from pendrive. I live mode and generally everything works well. So I started installation which also went well. After installing a reboot system, plugged out the pendrive and waited. Generally nothing happens. I see only the Dell logo and that’s all. After a long time the system goes into emergency mode. So It’s strange that with live mode everything works. After installation it’s sth broken. [/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri]With version 20.04 LTS I have the same situation. [/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri]Only version 18.04 works well. I mean that the booting process went fast, installation without problems and the system works. But it looks like Ubundu doesn’t support HDMI, screen bright options, and probably others thinks. I read that it lacks support for Intel Iris Xe Graphics.[/FONT][/COLOR][COLOR=#333333][FONT=Calibri]
[/FONT][/COLOR][COLOR=#333333][FONT=Calibri]
[/FONT][/COLOR][COLOR=#333333][FONT=Calibri]Please help me. I spent a lot of hours installing and trying different things. But nothing work. [/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri]
[/FONT][/COLOR]

---

### Post by TheFu on 2021-08-16
[https://www.phoronix.com/scan.php?page=news_item&px=Intel-Xe-MAX-dGPU-VM](https://www.phoronix.com/scan.php?page=news_item&px=Intel-Xe-MAX-dGPU-VM) says some ugly things. Appears they only got it working by layering the real host with a PCI passthru to a Linux KVM virtual machine so that 2 different kernels would be used.

> Again, not to be confused with integrated Xe-LP graphics on the likes of Tiger Lake that work out great on Linux without any fuss -- this is just about Xe MAX being in a primitive state for now on Linux.

Looks like the Try Ubuntu environment uses a different driver, probably Noveau, so for now (and this is a guess), you'll need to blacklist the intel iGPU driver.

[https://dgpu-docs.intel.com/devices/iris-xe-max-graphics/index.html](https://dgpu-docs.intel.com/devices/iris-xe-max-graphics/index.html) has a few suggestions. Basically, don't use the Max iGPU on the host machine, only inside virtual machines.
> In the meantime, we are excited to provide early access to that software and instructions to configure an Ubuntu 20.04.1 system so you can take advantage of both graphics adapters today. ... by running it exclusively connected to a guest VM.

Would help to see the exact hardware and driver used.  Can you ssh into the system?  Then you can gather hardware driver information without a working GPU. Do the same from a Try Ubuntu environment with 20.04.
**inxi -Gx**
is the command needed from both environments.

Does dmesg have a DRM error?
```
 dmesg | grep drm 
```

Looks like the fix may not come until 21.10 is released. In the meantime, running the newest, bleeding-edge, kernel might help to the iGPU drivers needed.  Read somewhere what 5.12.x is needed.  Perhaps getting the pre-Alpha version of 21.10 would be an option?

---

### Post by oldfred on 2021-08-16
Squeezing More Performance Out Of Intel Tiger Lake Xe Graphics By Using Mesa Git 21.04 
[https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git](https://www.phoronix.com/scan.php?page=news_item&px=TGL-Xe-Graphics-More-Mesa-Git)
Gen12 Xe Graphics might not be working out-of-the-box depending upon your kernel. 
Install OEM kernel
[https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372](https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372)
Re-booting the system while having "i915.force_probe=4c8a" Some distribution kernels including the likes of Ubuntu are already carrying the patch 
[https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=1)
Please don't mention i915.force_probe in end-user documentation #980 
[https://github.com/intel/media-driver/issues/980](https://github.com/intel/media-driver/issues/980) & 
[https://cateee.net/lkddb/web-lkddb/DRM_I915_FORCE_PROBE.html](https://cateee.net/lkddb/web-lkddb/DRM_I915_FORCE_PROBE.html)
[https://www.mail-archive.com/intel-gfx@lists.freedesktop.org/msg191190.html](https://www.mail-archive.com/intel-gfx@lists.freedesktop.org/msg191190.html)

when I built my then new system in early 2016, I had to install 16.04 before it was released to have newest kernel & drivers for support.
If willing to in effect be another tester, install 20.10. It will get many updates, so will need major housecleaning or reinstall after release.

---

### Post by ttmdear on 2021-08-16
[IMG]https://ibb.co/B3zYcnk[/IMG][COLOR=#333333][FONT=Calibri]Thanks for the reply. It seems too complex for a beginner like me :) [/FONT][/COLOR][COLOR=#333333][FONT=Calibri]
[/FONT][/COLOR][COLOR=#333333][FONT=Calibri]
[/FONT][/COLOR][COLOR=#333333][FONT=Calibri]Below I put the output of inix, xrandr and the printout of the message.which appeared when the system was trying to boot up.

[/FONT][/COLOR]\[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288997&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=288998&stc=1[/IMG]
[COLOR=#333333][FONT=Calibri][IMG]https://ibb.co/B3zYcnk[/IMG][/FONT][/COLOR]

---

### Post by oldfred on 2021-08-16
[https://dgpu-docs.intel.com/devices/hardware-table.html](https://dgpu-docs.intel.com/devices/hardware-table.html)
It looks like it will be 9a49 as shown above in screen shot.
>                      [TABLE="class: hardware-table"]
[TR]
[TD="align: left"]9A40, 9A49[/TD]
[TD="align: left"]Intel® Iris® Xe Graphics[/TD]
[TD="align: left"]Xe[/TD]
[TD="align: left"]Tiger Lake[/TD]
[/TR]
[/TABLE]


But please attach screen shots not post in line.
If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

---

### Post by TheFu on 2021-08-16
Ah, the risks of having bleeding edge hardware.  

With Linux, decades of use has taught me to get "new" hardware that is 2 yrs old for the least hassles. It also saves money.  Also learned that seeing "Linux Support" on a peripheral box could mean that it was supported by Linux 5+ yrs ago, but no more recent kernels, which means effectively ZERO Linux support.  Always check the hardware support DB before buying anything if you want it to work with Linux easily.

For example, I've been looking to build a new desktop/server. Even yr old motherboards have some poorly supported network chips in them, so I've decided to get a 2+ yr old motherboard instead.  Oddly, it isn't any cheaper, but it has the specific components that I want (Intel GigE NIC).  The newer MB has Intel 2.5Gbps NIC which should have great support by now, but doesn't. Looking through these forums, it is clear that the solution to that poor support is for people to buy a separate Intel GigE NIC and use that while they wait for better support --- eventually.

These rules of thumb apply for storage controllers, printers, scanners, and new GPUs.  Bleeding edge usually means hassles - even with CPUs! New CPUs can be problematic, sometimes.

But I have to admit, this is the first time I've seen a major hassle with an Intel iGPU. A number of my laptops have those and once, 7 yrs ago, 1 of the systems had a screen tearing problem with some videos. Besides that, the iGPUs from Intel were something we could count on working out of the box.

BTW, the **dmesg|grep drm** confirms the problem in the links.  For someone new to Linux, I'd say you should seek out local expertise from a LUG to get stuff setup.  Very few people will have come across this issue, so there will likely be some trial and error in the solution.  Running a new kernel is something I avoid unless there isn't any other choice. You really don't have another alternative, IMHO.

---

### Post by ttmdear on 2021-08-17
[COLOR=#333333][FONT=Calibri]It sounds like I have to switch to Win :( [/FONT][/COLOR][COLOR=#333333][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Calibri]I wonder why I can&#8217;t use a setup like this in the live version. Then it looks like it works in the minimal version which I need for now.[/FONT][/COLOR]

---

### Post by ttmdear on 2021-08-17
Is it possible to install with drivers which are used in live version?

---

### Post by dragonfly41 on 2021-08-17
I'm not sure is this line of thought will help .. I am on an earlier Dell 3268.
However, Microsoft now offers WSL2 on new generation PC's.
WSL2 is in fact a native image of Ubuntu within Windows 10.
But to me it seems a lot of hassle to get this working. I have tried WSL(1) which is Ubuntu bash only.
I am sticking with external SSD Ubuntu on USB 3.0 port.

---

### Post by TheFu on 2021-08-17
> **ttmdear said:**
> Is it possible to install with drivers which are used in live version?

The drivers are already installed there. Prevent the selected proprietary drivers from being used.  That's called "blacklisting" because there are blacklist files that do it.  It is worth a try.   /etc/modprobe.d/ is the directory.
Look at "blacklist-framebuffer.conf". 
fbdev is the framebuffer driver that doesn't work and only used as a fallback. It isn't blacklisted.  You still need to determine which driver is used during a live-boot/try ubuntu session.

A few posts ago, I wrote:
> Would help to see the exact hardware and driver used. Can you ssh into the system? Then you can gather hardware driver information without a working GPU. Do the same from a Try Ubuntu environment with 20.04.
**inxi -Gx**
is the command _**needed from both environments**_.

Since this wasn't provided, I assumed you weren't interested.

---

### Post by ttmdear on 2021-08-17
> **TheFu said:**
> 

Since this wasn't provided, I assumed you weren't interested.

I didn't notice this. Sorry. I'm really interested becaouse I don't want to install win and I'd like to use new device. 

```

workstati@latitude-5419:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
workstati@latitude-5420:~$ uname -r
5.4.0-42-generic
workstati@latitude-5420:~$ inxi -Gx
Graphics:  Device-1: Intel vendor: Dell driver: N/A bus ID: 0000:00:02.0 
           Display: x11 server: X.Org 1.20.11 driver: fbdev unloaded: modesetting,vesa resolution: 1920x1080~77Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.0.3 direct render: Yes 



```

I installed version also other OEM version but only 5.4.0-42 boot up.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288999&stc=1[/IMG]

---

### Post by ttmdear on 2021-08-20
@TheFu do you think about it? I mean that if this screen are ok.

---

### Post by TheFu on 2021-08-20
> **ttmdear said:**
> @TheFu do you think about it? I mean that if this screen are ok.

Sorry, I don't understand.  When it works, there is a driver, fbdev. That is short for framebuffer device (I guess).  When it doesn't work, there is a different driver (probably the bad intel driver).  Blacklist the Intel driver and the fbdev one should be used.  To blacklist, just follow the examples in the files in that same directory and reboot.

fbdev is not a great driver and will not perform well, but given the alternative is nothing, maybe it is the only choice for now.

If it was me and I was new to Linux and I had bought bleeding-edge, unsupported, hardware, then I'd run MS-Windows on the hardware and run Linux inside a virtual machine.  Running Linux full-screen on that CPU should fly. Plus, you wouldn't need to worry about drivers, since virtual machines only present the most compatible hardware to each VM.  I'd probably use VirtualBox as the hypervisor, but since I don't have Win10 and don't know if vbox works well on it, I'd be flexible with the hypervisor choice if that didn't work.  IMHO, VirtualBox is the least bad choice on Windows. **But it is what it is.**

I use VMs all day, every day.  My main Linux desktop is actually a VM running on a headless Linux server with KVM/Qemu, accessed over the network ... from anywhere in the world with internet. The last 1.5 yrs, that generally means a low-powered system using virt-viewer and SPICE. This setup is Linux-only. It can't be done on Windows.

---

### Post by ttmdear on 2021-08-23
Thank yours for your replies. 
 
I'm not so new. I've been using Linux for a few years but I've never had a need to dig into this part of the system. :) 
 
This idea vim VM seems like some compromise for now. I will read about this blacklist and try to do sth in this direction. Meantime I will be waiting for Ubundu 21.10. Maybe it will start working. I hope so.

---

