---
title: "GTX560 resolution issue, 12.10"
date: 2013-02-27
forum: General Help
---

### Post by dchambers811 on 2013-02-27
On a fresh install of 12.10 Secure Remix I have 5 Nvidia drivers to choose from: 310 & 304 experimental, nouveau, nvidia binary current & current-updates. Each one gives the same result -- all 4 sides of the screen extend an inch or more past the monitor's edges, no matter which resolution or driver is used.

The resolutions I have to choose from are:
1920x1080 @ 16:9 (unusable)
1280x720 @ 16:9 (default)
1176x664 @ 16:9 (added via xrandr)
1024x768 @ 4:3
1024x576 @ 16:9
800x600 @ 4:3

The monitor is a 32" sanyo tv connected via hdmi to a GTX560.

The 1280x720 setting is the least offensive; the other resolutions stretch the screen more than an inch off the monitor's edges. Does this have anything to do with the aspect ratio?

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1280x720       60.0*+
   1920x1080      30.0  
   1024x768       60.0  
   1440x480       30.0  
   1440x480i      30.0  
   1024x576       60.0  
   800x600        60.3  
   848x480        60.0  
   720x480        59.9  
   640x480        60.0     60.0     59.9  
   1176x664_59.90   59.9  
DP-1 disconnected (normal left inverted right x axis y axis)

``````
$ dpkg -l | grep -i nvidia*
rc  nvidia-current                            304.64-0ubuntu1~quantal~xup1              amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-current-updates                    304.51-0ubuntu1                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-experimental-304                   304.48-0ubuntu1                           amd64        Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-experimental-310                   310.14-0ubuntu1                           amd64        Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.64-0ubuntu1~quantal~xup1              amd64        Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-updates                   304.51-0ubuntu2                           amd64        Tool for configuring the NVIDIA graphics driver

```I can't find xorg.conf or I would post it. Any more info I can add, let me know. And thanks in advance.

---

### Post by dino99 on 2013-02-27
actual kernel directly deal with X, so its normal and prefered to not use xorg.conf (which can bring troubles if not set corectly). To be sure, run:

```
sudo rm /etc/X11/xorg.conf
```

then , from synaptic:

(if not already installed: sudo apt-get install synaptic)
- purge all the installed nvidia packages
- install that ppa to get the latest nvidia driver
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
- update & install : nvidia-313
-deactivate that ppa & update again
- reboot
):P

---

### Post by dchambers811 on 2013-02-27
> **dino99 said:**
>  - purge all the installed nvidia packages - install that ppa to get the latest nvidia driver [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) - update & install : nvidia-313 -deactivate that ppa & update again - reboot ):P

Thank you.

With 313 I can see the whole screen using 1024x768 @ 4:3, but have about 2 inches of black space running vertical along both sides of the display. No extra space horizontally.  At resolutions of 1920x1080 and 1280x720, there was no change -- the screen still extends an inch past the monitor's edges.

Edit: I cannot find the tv's remote so hopefully this can be resolved with the operating system.

Edit: The tv remote fixed the issue for Linux, but makes the Windows screen (dual boot system) smaller than usual. As soon as I can play Skyrim w/mods on Linux, it won't matter. :D

---

### Post by Regent45 on 2013-06-21
Nice choice. How do you intend to decide when to carry.

---

