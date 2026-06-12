---
title: "Where can I find video drivers?"
date: 2017-08-02
forum: General Help
---

### Post by jacatone on 2017-08-02
Been installing Lubuntu on older Pentium 4 machines but can't seem to find the necessary video drivers for older AGP video cards or integrated video. Is there a source somewhere for these drivers and codecs? I found this site below but it doesn't really say what to do once you've identified the video card and what is a mesa driver?


[http://www.cgl.ucsf.edu/chimera/graphics/updatelinux.html](http://www.cgl.ucsf.edu/chimera/graphics/updatelinux.html)

---

### Post by vocx on 2017-08-02
> **jacatone said:**
> Been installing Lubuntu on older Pentium 4 machines but can't seem to find the necessary video drivers for older AGP video cards or integrated video. Is there a source somewhere for these drivers and codecs? I found this site below but it doesn't really say what to do once you've identified the video card and what is a mesa driver?


[http://www.cgl.ucsf.edu/chimera/graphics/updatelinux.html](http://www.cgl.ucsf.edu/chimera/graphics/updatelinux.html)

The video drivers of a Linux distribution come with the Linux kernel. They are called kernel modules. These are all the files ending in ".ko", located in
```

/lib/modules/4.4.0-87-generic/kernel/drivers/video/

```

You typically do not need to install the modules themselves, except in special occasions. Use "lshw" to show your hardware.
```

sudo lswh -c video

*-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f0000000-f0ffffff memory:e0000000-efffffff ioport:4000(size=64)
  *-display
       description: 3D controller
       product: GM108M [GeForce 940M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:51 memory:f1000000-f1ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)

```

Use "lspci" to show which kernel module is available and in use for your hardware.
```

lspci -nnk

00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
    Subsystem: Lenovo Broadwell-U Integrated Graphics [17aa:5037]
    Kernel driver in use: i915
    Kernel modules: i915
04:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 940M] [10de:1347] (rev a2)
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375

```

As seen, the Intel card only uses the "i915" module. The Nvidia card uses the "nvidia" module, which actually is a collection of other modules.

The kernel will automatically chose the right module for you. Nowadays, there is usually only three types: Intel (integrated), Nvidia (discrete), or AMD/ATI (discrete). The Intel cards usually work without problems while with the Nvidia and AMD/ATI cards sometimes you need to get new drivers. Any other video card is usually old, is usually already using the best driver, and usually you won't be able to get any new drivers.

A "mesa" driver is an implementation of the OpenGL specification, basically for rendering 2D and 3D shapes in your screen. Old cards are not natively capable of "hardware rendering", so they use "software rendering" instead, which basically means that the video card is not very powerful. Nowadays, basically all cards have hardware acceleration, so talking about "mesa" drivers is mostly irrelevant. All have such capabilities.

You should check the output of "lshw" and "lspci" to really know what kernel module you are using. I don't know the interface in Lubuntu (LXDE?), but in the regular Settings menu in Unity you can go to Settings > Software and updates > Additional drivers. It will search your system and tell you if there are proprietary drivers to install; these are normally for Nvidia or AMD/ATI cards. I'm afraid that if you use another brand that is not Intel, Nvidia, or AMD/ATI, you may have no other choice of kernel driver than the one you are already using.

---

### Post by ajgreeny on 2017-08-03
Are you having problems and if so what are they, or are you still thinking like a Windows user where you generally try to keep drivers updated as much as possible?

As vocx says, you do not normally need to install drivers for graphic cards separately unless you have a problem with video playing.  You could, however, with such an old CPU be finding that the resources available are pretty minimal as far as graphic are concerned, particularly if trying to play HD videos at high resolutions, and you may need to consider either better hardware or lower resolution videos.

---

### Post by jacatone on 2017-08-07
I guess Linux moves forward like hardware. Don't have any video resolution problems with core2duo or i3 Intel machines. Seems a shame not to repurpose older hardware when it works fine.

---

### Post by vocx on 2017-08-07
> **jacatone said:**
> I guess Linux moves forward like hardware. Don't have any video resolution problems with core2duo or i3 Intel machines. Seems a shame not to repurpose older hardware when it works fine.
I don't understand what you are saying here. Do you mean your hardware is no longer supported? Or that you confirmed you cannot install new drivers?

Linux moves forward with hardware, this is true. But older hardware drivers are still available in the kernel, so your device, even if old, should still be supported. This is one of the strengths of Linux, that it provides compatibility to a thousand different devices, even old ones.

---

### Post by sonicwind on 2017-08-07
vocx - That was a nice tutorial above. Thank you.

---

### Post by jacatone on 2017-08-11
I find newer versions of Linux won't even install on older hardware like P4 and Pentium D machines. If they do install the resolution is usually 800x400 and not the default 1920x1080. I'm simply trying to find these old linux legacy video drivers for integraded, nvidia and ati cards and how to install them?

---

### Post by vocx on 2017-08-12
> **jacatone said:**
> I find newer versions of Linux won't even install on older hardware like P4 and Pentium D machines. If they do install the resolution is usually 800x400 and not **the default 1920x1080.** I'm simply trying to find these old linux legacy video drivers for integraded, nvidia and ati cards and how to install them?
Default resolution of what? Of the monitor? Of the video card?

If the system is old, as you say, probably it won't show resolutions above 1024x768, simply because that resolution was not available then. You cannot magically force an old video card, that has a hardware limitation, to display the high resolutions we have today. That's like asking a VHS tape to show Blue Ray quality by putting it in a brand new VCR.

Your question is still vague. Which exactly are these Nvidia and ATI cards that you want to keep running? The only possible way to find if the device is supported is to know the part number or model. Just saying, "I have old cards, where drivers, download, install?" is not going to work, because the "drivers" are tightly integrated into the Linux kernel and the display server, namely Xorg. At least now you mention that those old cards are Nvidia and ATI, which you did not mention in your original post.

Cards from Nvidia are supported by the proprietary "nvidia" module, which can be installed from the Ubuntu settings. However, there is also the open source "nouveau" driver. As far as I know, newer cards are intended to work with the "nvidia" driver. The "nouveau" driver is an alternative for those that want to use free software, and apparently it also supports older cards. That is, a card may not work at all with "nvidia", but it may work with the "nouveau" module. These two come with Ubuntu so you don't need to go to some website, get the source, and somehow install them that way. The drivers can be simply installed with the Setting > Software and updates > Additional drivers dialogue.

Cards from AMD/ATI are supported by the proprietary "amdgpu" and "amdgpu-pro" modules. There is also the open source "radeon" driver. The same as with Nvidia, some older cards are only supported by the "radeon" driver and not the more modern "amdgpu" modules. Formerly, the proprietary driver was the "fglxr" or "Catalyst" driver. It seems now it's unsupported because AMD decided to drop support for it.

The problem with the support of old video cards is that the companies themselves did not do much to support their own devices until more recently with the "nvidia" and "amdgpu" modules. So, it may just be that older hardware don't run well. If it were a regular Ethernet card, USB controller, or keyboard, you can bet those things don't change much so the kernel will support them forever. With video cards, however, it is tightly integrated into other things like the X Server (Xorg), the Open GL libraries, the Linux kernel, etc., so it requires tight maintenance.

I want to tell you that your options are limited. Basically, you find out if the pre-packaged drivers "nouveau" and "radeon" work or not, and that's it; then you decide if that is good enough for you, or you decide to stop using that old hardware. You will have very little chance of getting better drivers, or even old, "legacy" drivers that "used to work back then", because things have changed, the kernel has changed, Xorg has changed, so it'd be a monumental task to make it work just for one driver. Basically, you'd need to get the entire Linux kernel, Xorg, OpenGL libraries, and whatever other dependencies, and recompile everything again, and hope it works without breaking many other things that depend on them.

Read these
[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
[https://askubuntu.com/questions/294994/why-does-the-amd-proprietary-graphics-driver-not-support-old-cards](https://askubuntu.com/questions/294994/why-does-the-amd-proprietary-graphics-driver-not-support-old-cards)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

