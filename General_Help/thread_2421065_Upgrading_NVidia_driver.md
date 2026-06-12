---
title: "Upgrading NVidia driver"
date: 2019-06-15
forum: General Help
---

### Post by Edward_Diener on 2019-06-15
I was not able to upgrade Ubuntu 18.04 to 18.10 due to an NVidia driver problem when rebooting into 18.10. So I have decided to try to upgrade my NVidia driver on Ubuntu 18.04 first to see if that does not solve my original problem. My graphics card is the GeForce GTX 960. I first added the [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) repository to get the latest supported drivers. On the "Software & Updates" "Additional Drivers" tab it now shows the GeForce GTX 960 additional drivers as choices for me to make. However I have not manually installed a new particular driver among these additional drivers. Do I need to do so ? If I just choose the latest of them for my graphics card and click the "Apply Changes" button, it says that it is working on the change but it seems as if nothing further actually happens, no matter how long I wait.

What is the proper way of upgrading my NVIdia driver from among those offered in the [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) repository ?

---

### Post by Bashing-om on 2019-06-15
Edward_Diener; Welp;

When release-upgrading you want to get back to as close to a default install as possible, That means too to revert the graphic's driver to nouveau (open source driver). Once the upgrade is done then install the proper driver for your card.
In the case of the GTX960 Nvidia recommends the 430 version:
[https://www.nvidia.com/Download/driverResults.aspx/148435/en-us](https://www.nvidia.com/Download/driverResults.aspx/148435/en-us)
Which I can accept is only available from the PPA.

See:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)

[INDENT]there is a path that seems right
[INDENT][INDENT]but leads to a borked system
[/INDENT][/INDENT][/INDENT]

---

### Post by Edward_Diener on 2019-06-15
> **Bashing-om said:**
> Edward_Diener; Welp;

When release-upgrading you want to get back to as close to a default install as possible, That means too to revert the graphic's driver to nouveau (open source driver). Once the upgrade is done then install the proper driver for your card.
In the case of the GTX960 Nvidia recommends the 430 version:
[https://www.nvidia.com/Download/driverResults.aspx/148435/en-us](https://www.nvidia.com/Download/driverResults.aspx/148435/en-us)
Which I can accept is only available from the PPA.

See:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)
[INDENT]there is a path that seems right[INDENT][INDENT]but leads to a borked system
[/INDENT]
[/INDENT]
[/INDENT]


The nouveau driver gives me a 640 x 400 display, which is not even good enough to upgrade from 18.04 to 18.10 as the screen gets cut off..

I can see the NVidia 430 version. How do I choose it ? When I tried in 18.04, in the Additional Drivers tab as explained above, the upgrade process stalled.

---

### Post by Bashing-om on 2019-06-15
Edward_Diener; Hey -

I say again that you can not release-upgrade with a proprietary driver installed,
> 
The nouveau driver gives me a 640 x 400 display, 

With nouveau installed in that condition we do need to find out the why.

else one can do a clean fresh install and be done with it all,

[INDENT]alternate path to an end
[/INDENT]

---

### Post by CatKiller on 2019-06-15
> **Edward_Diener said:**
> What is the proper way of upgrading my NVIdia driver from among those offered in the [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) repository ?
The nvidia drivers don't upgrade cleanly from one branch to another. So if you're on the 410 branch, say, then the updates that you get will work fine. But switching to a different branch, like 418 or 430, breaks things. I have no idea if it's an nvidia issue, or the way they're packaged by the PPA maintainers, or something else, but it just doesn't work.

Because of that, the way to update the drivers means that you need to pull up the terminal. Installing for the very first time is probably fine from the automatic tool, but if you've already got a version of the proprietary driver installed you need to use the terminal to purge it and reinstall the new one.

I'm typing on my phone, so I can't check the syntax for you, but it's something along the lines of ```
sudo apt purge nvidia*
sudo apt install nvidia-graphics-drivers-430
```

Also of note is that, for some reason, switching branches always makes my shutdown widget not work for the rest of the session. If that happens to you, ```
sudo shutdown -r now
``` will restart your computer.

As bashing-om says, if your primary objective is to upgrade the whole OS, you'll be best served by *removing* all your PPAs, to get as close as you can be bothered to a default install. **ppa-purge** is a useful tool for that.

Installing the newer version of the driver would be what you'd do if you were sticking with the LTS version, and wanted the features of the newer driver. That is exactly what I'd suggest that you do: upgrading to 18.10 means that you need to upgrade **again** in a month's time because 18.10 goes End Of Life then. And then **again** within the next six months. And then **again**. By contrast, 18.04 is supported until 2023. Interim releases are for people that love to test software.

---

### Post by CatKiller on 2019-06-15
> **Bashing-om said:**
> With nouveau installed in that condition we do need to find out the why.
That's easy: nouveau struggles to do modesetting. Nvidia could help, but they don't.

---

### Post by Edward_Diener on 2019-06-15
> **Bashing-om said:**
> Edward_Diener; Hey -

I say again that you can not release-upgrade with a proprietary driver installed,

With nouveau installed in that condition we do need to find out the why.

else one can do a clean fresh install and be done with it all,
[INDENT]alternate path to an end
[/INDENT]


As I explained above it is impossible to even upgrade with the 640 x 400 screen of the nouveau driver. All windows get cut off at the bottom of the screen and it is impossible to even see what is there much less do an upgrade with that sort of display. If i knew how to change to a decent size screen after switching to the nouveau driver I would do it.

---

### Post by Edward_Diener on 2019-06-15
> **CatKiller said:**
> The nvidia drivers don't upgrade cleanly from one branch to another. So if you're on the 410 branch, say, then the updates that you get will work fine. But switching to a different branch, like 418 or 430, breaks things. I have no idea if it's an nvidia issue, or the way they're packaged by the PPA maintainers, or something else, but it just doesn't work.

Because of that, the way to update the drivers means that you need to pull up the terminal. Installing for the very first time is probably fine from the automatic tool, but if you've already got a version of the proprietary driver installed you need to use the terminal to purge it and reinstall the new one.

I'm typing on my phone, so I can't check the syntax for you, but it's something along the lines of ```
sudo apt purge nvidia*
sudo apt install nvidia-graphics-drivers-430
```

Also of note is that, for some reason, switching branches always makes my shutdown widget not work for the rest of the session. If that happens to you, ```
sudo shutdown -r now
``` will restart your computer.

As bashing-om says, if your primary objective is to upgrade the whole OS, you'll be best served by *removing* all your PPAs, to get as close as you can be bothered to a default install. **ppa-purge** is a useful tool for that.

Installing the newer version of the driver would be what you'd do if you were sticking with the LTS version, and wanted the features of the newer driver. That is exactly what I'd suggest that you do: upgrading to 18.10 means that you need to upgrade **again** in a month's time because 18.10 goes End Of Life then. And then **again** within the next six months. And then **again**. By contrast, 18.04 is supported until 2023. Interim releases are for people that love to test software.

As explained above switching to the nouveau driver give sme a 640 x 400 screen and all windows get cut off at the bottom, so it is impossible for me to upgrade at that resolution. If I could change the resolution once I switch back to the nouveau driver to something I could work with I would. The only reason  I am trying to update to 18.10 is because I can then update to 19.04. I see no path to update from 18.04 to 19.04.

---

### Post by Bashing-om on 2019-06-15
Edward_Diener; 

Let us take a poke then at fixing that display presentation.

What have we now for a driver ?
Post back the results:
```

sudo lshw -C dispaly
dpkg -l | grep -i nvidia
lsmod | grep nvidia
lsmod | grep nouveau

```

If at the login screen you activate a console interface (ctl+alt+F2), do you here have good resolution?

see if if we go looking at log files.

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by Edward_Diener on 2019-06-16
> **Bashing-om said:**
> Edward_Diener; 

Let us take a poke then at fixing that display presentation.

What have we now for a driver ?
Post back the results:
```

sudo lshw -C dispaly
dpkg -l | grep -i nvidia
lsmod | grep nvidia
lsmod | grep nouveau

```

If at the login screen you activate a console interface (ctl+alt+F2), do you here have good resolution?

see if if we go looking at log files.[INDENT][INDENT]got to be a reason
[/INDENT]
[/INDENT]


```
sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: GM206 [GeForce GTX 960]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:130 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff
```

```
dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64                   390.116-0ubuntu0.18.04.1                     amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                       390.116-0ubuntu0.18.04.1                     all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                390.116-0ubuntu0.18.04.1                     amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                 390.116-0ubuntu0.18.04.1                     i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                 390.116-0ubuntu0.18.04.1                     amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                  390.116-0ubuntu0.18.04.1                     i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                 390.116-0ubuntu0.18.04.1                     amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                  390.116-0ubuntu0.18.04.1                     i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                   390.116-0ubuntu0.18.04.1                     amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                    390.116-0ubuntu0.18.04.1                     i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                     390.116-0ubuntu0.18.04.1                     amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                      390.116-0ubuntu0.18.04.1                     i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                   390.116-0ubuntu0.18.04.1                     amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                    390.116-0ubuntu0.18.04.1                     i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-375                                 384.130-0ubuntu0.17.10.1                     amd64        Transitional package for nvidia-384
ii  nvidia-384                                 390.116-0ubuntu0.18.04.1                     amd64        Transitional package for nvidia-driver-390
ii  nvidia-compute-utils-390                   390.116-0ubuntu0.18.04.1                     amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                            390.116-0ubuntu0.18.04.1                     amd64        NVIDIA DKMS package
ii  nvidia-driver-390                          390.116-0ubuntu0.18.04.1                     amd64        NVIDIA driver metapackage
ii  nvidia-headless-no-dkms-390                390.116-0ubuntu0.18.04.1                     amd64        NVIDIA headless metapackage - no DKMS
ii  nvidia-kernel-common-390                   390.116-0ubuntu0.18.04.1                     amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                   390.116-0ubuntu0.18.04.1                     amd64        NVIDIA kernel source package
rc  nvidia-opencl-icd-375                      384.90-0ubuntu0.17.04.2                      amd64        Transitional package for nvidia-opencl-icd-384
rc  nvidia-opencl-icd-384                      390.48-0ubuntu3                              amd64        Transitional package for nvidia-headless-390
ii  nvidia-prime                               0.8.8.2                                      all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            390.77-0ubuntu0.18.04.1                      amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                           390.116-0ubuntu0.18.04.1                     amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390              390.116-0ubuntu0.18.04.1                     amd64        NVIDIA binary Xorg driver

```

```
lsmod | grep nvidia
nvidia_uvm            757760  0
nvidia_drm             40960  2
nvidia_modeset       1048576  11 nvidia_drm
nvidia              14376960  482 nvidia_uvm,nvidia_modeset
drm_kms_helper        167936  1 nvidia_drm
drm                   401408  5 drm_kms_helper,nvidia_drm
ipmi_msghandler        53248  2 ipmi_devintf,nvidia

```

lsmod | grep nouveau produces nothing.

---

### Post by monkeybrain20122 on 2019-06-16
You can't "upgrade" with the Nvidia driver so you have to uninstall it, upgrade then reinstall the Nvidia driver. But why even bother?? Just back up your data and do a clean install, a lot faster and easier.

---

### Post by CatKiller on 2019-06-16
> **Edward_Diener said:**
> As explained above switching to the nouveau driver give sme a 640 x 400 screen and all windows get cut off at the bottom, so it is impossible for me to upgrade at that resolution. If I could change the resolution once I switch back to the nouveau driver to something I could work with I would. The only reason  I am trying to update to 18.10 is because I can then update to 19.04. I see no path to update from 18.04 to 19.04.
You don't need to use the windows to upgrade, you can do it from the command line. Either a terminal or TTY. I'm pretty sure the command is **do-release-upgrade**.

You'll be able to upgrade straight from 18.04 to 19.04 after 18.10 has been end-of-lifed.

Again, I'd recommend staying on the LTS release.

---

### Post by Bashing-om on 2019-06-16
Edward_Diener; Ho-Kay

The "dpkg -l | grep -i nvidia" output shows that there is a driver conflict. System has no idea of which driver to use.

Let's begin the clean up and prep to properly re-install the driver,
show us:
```

cat /etc/X11/Xorg.conf
ls -al /usr/share/X11/xorg.conf.d/*.conf

```

However, if it is the desire to continue on to the 18.10 release, then we want to remove the proprietary graphic's drivers, and make sure that nouveau is then functional.

[INDENT][INDENT]the call is yours
[/INDENT][/INDENT]

---

### Post by Edward_Diener on 2019-06-17
> **Bashing-om said:**
> Edward_Diener; Ho-Kay

The "dpkg -l | grep -i nvidia" output shows that there is a driver conflict. System has no idea of which driver to use.

Let's begin the clean up and prep to properly re-install the driver,
show us:
```

cat /etc/X11/Xorg.conf
ls -al /usr/share/X11/xorg.conf.d/*.conf

```

However, if it is the desire to continue on to the 18.10 release, then we want to remove the proprietary graphic's drivers, and make sure that nouveau is then functional.
[INDENT][INDENT]the call is yours
[/INDENT]
[/INDENT]


I was able to install the latest proprietary graphic driver, 430 instead of 390, for my GeForce GTX 960 from ppa:graphics-drivers/ppa. My problem with the nouveau driver is that it does not recognize my monitor and so works in only 640 x 400 mode, which is ancient and ridiculous to deal with. No one should have to switch to a 640 x 400 screen just to upgrade a release. I also do not understand why I would need to remove all the proprietary drivers just to use the nouveau driver. The Additional Drivers page provides a way to switch between any of the NVidia proprietary drivers and the nouveau driver without having to remove anything. But as far as the nouveau driver it is hopeless.  I can't even install the latest nouveau driver offered by 18.04, for some reason, in the hopes of fixing the ridiculous 640 x 400 problem.

---

### Post by CatKiller on 2019-06-17
> **Edward_Diener said:**
> I was able to install the latest proprietary graphic driver, 430 instead of 390, for my GeForce GTX 960 from ppa:graphics-drivers/ppa. My problem with the nouveau driver is that it does not recognize my monitor and so works in only 640 x 400 mode, which is ancient and ridiculous to deal with. No one should have to switch to a 640 x 400 screen just to upgrade a release. I also do not understand why I would need to remove all the proprietary drivers just to use the nouveau driver. The Additional Drivers page provides a way to switch between any of the NVidia proprietary drivers and the nouveau driver without having to remove anything. But as far as the nouveau driver it is hopeless.  I can't even install the latest nouveau driver offered by 18.04, for some reason, in the hopes of fixing the ridiculous 640 x 400 problem.

You should slow down.

You don't need to *install* the nouveau driver. The kernel bits are already part of the kernel, and the non-kernel bits are already part of Mesa. Installing the proprietary driver configures those parts to not be used and removing the proprietary driver, ideally, configures those parts to be used again.

The Additional Drivers page *doesn't* provide a way to switch between the drivers without adding or removing anything. It's exactly the same packages, running exactly the same scripts, as doing so directly through the package manager. It also comes with exactly the same flaws as installing the packages any other way, with the added wrinkle that you don't get to see Terminal output.

The nouveau driver isn't as good at auto-detecting screen modes as the proprietary driver. Nvidia could help with that, but they don't. It is still possible to configure screen modes manually with the nouveau driver, but most people don't bother because they want the proprietary driver anyway.

You don't *have* to remove the PPAs and their packages before doing the upgrade, but having random and untested mix-and-matched package versions sharply increases your chances of having a botched upgrade. As you've already done.

It takes moments to start the upgrade from the command line, and then you can wander off and do something else, which means you don't have to look at that painful VGA resolution any more. Heck, you can do it from your phone and never look at your monitor at all.

None of us here are Ubuntu developers, or nouveau developers, or Nvidia developers, or package maintainers, or in any way responsible for the software or its configuration on your computer. We are volunteers offering knowledge to help you out, for free. Try to keep your frustration in check.

I'll also mention, again, that sticking with the LTS releases is, by far, the best solution for you. Particularly if you would find merely having a sub-optimal resolution for maybe an hour so frustrating, using the guinea pig releases doesn't seem like a good fit for your temperament.

---

### Post by Edward_Diener on 2019-06-17
> **CatKiller said:**
> You should slow down.

You don't need to *install* the nouveau driver. The kernel bits are already part of the kernel, and the non-kernel bits are already part of Mesa. Installing the proprietary driver configures those parts to not be used and removing the proprietary driver, ideally, configures those parts to be used again.

The Additional Drivers page *doesn't* provide a way to switch between the drivers without adding or removing anything. It's exactly the same packages, running exactly the same scripts, as doing so directly through the package manager. It also comes with exactly the same flaws as installing the packages any other way, with the added wrinkle that you don't get to see Terminal output.

The nouveau driver isn't as good at auto-detecting screen modes as the proprietary driver. Nvidia could help with that, but they don't. It is still possible to configure screen modes manually with the nouveau driver, but most people don't bother because they want the proprietary driver anyway.

You don't *have* to remove the PPAs and their packages before doing the upgrade, but having random and untested mix-and-matched package versions sharply increases your chances of having a botched upgrade. As you've already done.

It takes moments to start the upgrade from the command line, and then you can wander off and do something else, which means you don't have to look at that painful VGA resolution any more. Heck, you can do it from your phone and never look at your monitor at all.

None of us here are Ubuntu developers, or nouveau developers, or Nvidia developers, or package maintainers, or in any way responsible for the software or its configuration on your computer. We are volunteers offering knowledge to help you out, for free. Try to keep your frustration in check.

I'll also mention, again, that sticking with the LTS releases is, by far, the best solution for you. Particularly if you would find merely having a sub-optimal resolution for maybe an hour so frustrating, using the guinea pig releases doesn't seem like a good fit for your temperament.

I am just trying to upgrade from 18.04 to 18.10 so that I can subsequently upgrade from 18.10 to 19.04. I am not interested in non-LTS releases. If Ubuntu offered a way to skip the non-LTS release 18.10 in order to go from 18.04 to 19.04 I would have tried that.

Let's say I switch to the nouveau driver for the purposes of the upgrade. How can I configure the nouveau driver manually so that it gives me something other than 640 x 400 resolution ? I usually run 1920 x 1080 resolution.

---

### Post by CatKiller on 2019-06-17
> **Edward_Diener said:**
> I am just trying to upgrade from 18.04 to 18.10 so that I can subsequently upgrade from 18.10 to 19.04. I am not interested in non-LTS releases. If Ubuntu offered a way to skip the non-LTS release 18.10 in order to go from 18.04 to 19.04 I would have tried that.

19.04 isn't an LTS release, either. The next LTS is 20.04.

> Let's say I switch to the nouveau driver for the purposes of the upgrade. How can I configure the nouveau driver manually so that it gives me something other than 640 x 400 resolution ? I usually run 1920 x 1080 resolution.

By adding either sufficient EDID (or EDID-like, from the monitor manual) information so that the resolution can be automatically determined (HorizSync and VertRefresh ranges are normally sufficient) or a full Coordinated Video Timings modeline from xrandr, and putting that in your xorg.conf. It's your BIOS that sets the resolution to 640×480, and nothing else is confident enough to set it to something else without breaking your monitor, so it doesn't. Nvidia's driver seems to have some special sauce for getting EDID out of monitors that the nouveau driver lacks.

---

