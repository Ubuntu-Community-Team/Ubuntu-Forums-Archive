---
title: "Nvidia Video Tearing"
date: 2014-07-20
forum: General Help
---

### Post by mooreted on 2014-07-20
Running Ubuntu 14.04 x64 with Nvidia GTX 650 and driver version: 331.38

This is weird: When I watch any video in Unity, Xfce (with or without compositing, with or without compton) and OpenBox I get video tearing. I do not get video tearing in Fluxbox. 

In compiz I have set Vsync, force redraw, undirect full-screen windows and set the refresh rate to 60mhz. I have turned off flipping and enabled Vsync in nvidia-settings.

Why would Fluxbox work when no other does? Maybe I'll just switch to Flux.

---

### Post by mooreted on 2014-07-20
Ok, it gets even weirder. In Fluxbox, if I run xfce4-panel the video tearing comes back. No video tearing with stock Fluxbox. This makes no sense.

---

### Post by mooreted on 2014-07-21
Upgraded to Nvidia 340.24, no change. I guess I'll just have to put up with it.

---

### Post by mc4man on 2014-07-21
Appears to be fairly common with kepler chips, maybe something in here will alleviate..
[https://devtalk.nvidia.com/default/topic/543305/linux/screen-video-tearing-gtx6xx-7xx-titan-kepler-maxwell-in-almost-all-applications-including-desktop/1/](https://devtalk.nvidia.com/default/topic/543305/linux/screen-video-tearing-gtx6xx-7xx-titan-kepler-maxwell-in-almost-all-applications-including-desktop/1/)
(I no longer have a desktop, on my optimus laptops, 660m & 775m, nvidia thru nvidia-prime is worthless due to tearing everywhere so I  just use Intel in linux sessions.

---

### Post by mooreted on 2014-07-21
Thanks, I'll check it out. It does seem to be a very common problem.

---

### Post by mooreted on 2014-07-21
Ok, took some doing, but I fixed it as follows:

Open a CLI and do:

sudo nvidia-xconfig

Then:

sudo nvidia-settings

Set your screen resolution and refresh rate in the Xserver settings (I set mine to 1920x1200 @60hz) and save it to xorg.conf

Then do:

sudo nano /etc/X11/xorg.conf

Edit the device section thusly:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 650"
    Option "RegistryDwords" "PerfLevelSrc=0x2222"
    Option "TripleBuffer" "True"
EndSection

This sets the card to performance mode and enables triple buffering.

In nvidia-settings/OpenGL set:

Sync to Vblank
Allow Flipping
Use Conformant Texture Clamping

Save your configuration and restart the X-server.

---

### Post by BODYPRINT on 2014-10-17
Thanks mooreted.

That worked great!

---

### Post by mooreted on 2014-10-17
> **BODYPRINT said:**
> Thanks mooreted.

That worked great!

You are welcome. Glad I could help. Happy computing.

---

### Post by rqm91 on 2014-12-13
PerfLevelSrc=0x2222 sets performance level to a fixed performance level, better to use PerfLevelSrc=0x2233 instead, otherwise your graphics card will be set to the MAX level with a higher minimum clock frequency and a higher minumum transfer rate which may cause overheating. Anyway, enabling tripple buffering fixed my tearing problem, thanks.

---

