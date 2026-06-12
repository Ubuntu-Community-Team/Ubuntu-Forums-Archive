---
title: "How to change resolution of 640x480 during Live USB installation?"
date: 2022-11-18
forum: General Help
---

### Post by xanizen on 2022-11-18
Before getting to the install screen, I had press 'E', then enter modeset after 'quiet splash'
[https://askubuntu.com/a/1059144](https://askubuntu.com/a/1059144)

But then screen resolution is 600x480, and I can't see the Next/Back button. I also can't move the window up, only left right or down. Another problem with this, is configuring the partitions is almost impossible.

I did xrandr and got the following output:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm
    640x480         0.00*
```

I tried to add custom resolution following the instructions here, [https://askubuntu.com/a/377944](https://askubuntu.com/a/377944), but the step:
```
xrandr --addmode VGA-0 1680x1050_60.00
```

Is a gridlock. As seen from the xrandr, there is no VGA output, the monitor is connected with a DVI cable, also DVI-0 or DVI-1 was not accepted.

xrandr --listproviders outputs:
Providers: number: 0

xrandr --listactivemonitors output:
```
xrandr: Failed to get size of gamma for output default
Monitors: 1
0: +*default 640/169x480/127+0+0 default
```

The following was accepted:
```
xrandr --addmode default 800x600_60.00
```
Generating output: xrandr: Failed to get size of gamme for output default

xrandr -q, now includes 800x600:
```

xrandr: failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 800 x 600
default connected primary 640x480+0+0 0mm x 0mm
   640x480            0.00*
   800x600_60.00  59.86 

```

But then executing, xrandr --output default --mode 800x600_60.00 generated:
```

xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

The motherboard is from the year 2008 with an Intel 965 chipset. Graphics card is nVidia 7800gt.

---

### Post by xanizen on 2022-11-19
I succeeded in using the window key to move the window around to successfully install it.

To log into the install OS, I had to then press and hold the shift key after the BIOS splash, AND once the the white text appears that typically lists the input streams/devices (PRE-grub) boot loader. Then modify grub bootloader for ubuntu and add 'nomodeset'.

The 640x480 resolutions persists. Also the 304 nVidia factory driver are not compatible/permitted for installation by Ubuntu.

I already ensured nouveau drivers were the latest with 'sudo apt install xserver-xorg-video-nouveau', and that didn't do anything.

---

