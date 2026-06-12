---
title: "Radeon HD 6520G driver for Notebook"
date: 2016-09-04
forum: General Help
---

### Post by thedoors67 on 2016-09-04
Hello, so this is my first forum post. I just installed a new SSD on my laptop which was out of use due to dead HDD. I used a bootable-usb to install Ubuntu 16.04 on it, and after the initial setup, I restarted the laptop. It just booted to a black screen but I heard the audio queue to enter login password. Basically, I believe I've identified that I need the correct video card driver for this laptop in order for it to work. It's a Radeon HD 6520G. I tried installing a driver already from the AMD website but it did not work, I don't even think I did it right. Anyway, any help is appreciated, thank you.

P.S. I am new to Linux based OS but I do know lots about troubleshooting and the command prompt on Windows, so please bear with me if I don't understand how to do some things.

---

### Post by ajgreeny on 2016-09-04
The proprietary driver for AMD graphics does not work with 16.04 (at the moment) though it may arrive and be useable in future as AMD are working on their graphics drivers for linux quite hard at present.

It's a case of watch this space and keep hoping, but until it all starts to happen you will be able to use only the default drivers that were used after installation of the OS.

Quote from the Release Notes for 16.04, [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
> Graphics and Display

fglrx

The fglrx driver is now deprecated in 16.04, and we recommend its open source alternatives (radeon and amdgpu). AMD put a lot of work into the drivers, and we backported kernel code from Linux 4.5 to provide a better experience.

When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

---

### Post by thedoors67 on 2016-09-04
Okay I see. About two days ago I tried to install the fglrx driver. But that didn't work obviously. So what should I do now? I'm pretty sure that driver is installed somewhere, should I try to get rid of it? And after I do, do I just have to keep booting up with nomodeset, or can I try to switch it to the default amdgpu or radeon driver?

---

### Post by bainespal on 2016-09-04
> **thedoors67 said:**
> I'm pretty sure that driver is installed somewhere, should I try to get rid of it? And after I do, do I just have to keep booting up with nomodeset, or can I try to switch it to the default amdgpu or radeon driver?

I'm struggling with a similar issue (haven't fixed it yet) --- from my research it appears that the answer to your first question is clear. If you're using Ubuntu 16.04 and your desktop environment was broken by trying to install fglrx, you definitely need to get rid of fglrx. I've already done so with the command ```
[COLOR=#333333]sudo apt-get remove --purge xorg-driver-fglrx fglrx*[/COLOR]
``` as shown [here]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx").

I think the answer to your second question is that the surest bet is to use the default open source driver called **radeon**. (Though this might depend on your video card.) [This wiki page]("https://help.ubuntu.com/community/RadeonDriver") says that the radeon driver comes pre-installed, which is all well and good, but it doesn't say how to re-active it after a failed installation of fglrx. I don't know if my radeon driver has been uninstalled, and I don't know what it's package name is in order to try re-installing it with **apt-get**. The package name "radeon" is not [listed]("http://packages.ubuntu.com/xenial/allpackages") in the directory of packages for Ubuntu 16.04!

Can you at least get into a terminal? After you've turned your notebook on and given it enough time to load the login screen, does pressing **Ctrl + Alt + F2 **bring you to a terminal login?

If so, I think the command we need to use to get information for other people to help us is **sudo lshw -C display**.

In my case, this is the output, and I know the part that says "display UNCLAIMED" is bad business, but I don't know how to have the supposedly present radeon driver claim the display:
```
*-display UNCLAIMED
       description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0000000-f001ffff ioport:1100(size=256) memory:f0040000-f005ffff
```

Good luck!

---

