---
title: "Crashing at login screen and black flashes"
date: 2016-05-18
forum: General Help
---

### Post by 4vrdeth on 2016-05-18
I recently built a desktop with Kubuntu 15.10 64bit to be a media PC/server. It has never been fully stable randomly freezing. I recently added Nvidia drivers and Compiz and now it's started to get annoyingly unstable but still random. I've been trying for the last week to figure out how to troubleshoot this but i'm learning as I go the whole time. Any help to get this stable would greatly be appreciated. current known isssues:

1. X11 freezes up. Most of the time I can free it up with crtl/alt/backspace although it usually takes a bit. I can access via SSH but don't know what to look for, most of the time I have to use SysRq or hard boot it

2. i get random black screen flashes. usually happens 2 or 3 times during the login boot splash, and at random points will using the desktop.

3. After running it for a while the desktop will crash, exiting to the login screen.once there I can try to log back in but, it will black out and reset the login screen.

4. setting KDE compatibility mode in CCSM seems to fix issue #1 and #2 but, then Kmenu stops working. it'll flash open and close, or it'll open and it won't go away. 

desktop specs
intel Q6600 2.4ghz
4GB ddr2 800
gigabyte P41T-ES3G
Geforce gt 710

---

### Post by 4vrdeth on 2016-05-21
sorry if my post was a bit vague. I took some time to investigate and copied a xorg.log for each crash. 

#1 I haven't found a specific way to get this freeze occur. As i suspected its Nvidia issuse, and it doesn't respond to resetting x11. This is the end of Xorg.0.log
> [ 534.069] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): connected[ 534.070] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): Internal TMDS
[ 534.070] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): 340.0 MHz maximum pixel clock
[ 534.070] (--) NVIDIA(GPU-0): 
[ 534.071] (--) NVIDIA(GPU-0): CRT-0: disconnected
[ 534.071] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[ 534.071] (--) NVIDIA(GPU-0): 
[ 534.071] (--) NVIDIA(GPU-0): DFP-0: disconnected
[ 534.071] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[ 534.071] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[ 534.071] (--) NVIDIA(GPU-0): 
[ 534.099] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): connected
[ 534.099] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): Internal TMDS
[ 534.099] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): 340.0 MHz maximum pixel clock
[ 534.099] (--) NVIDIA(GPU-0): 
**(EE) [mi] EQ overflowing. Additional events will be discarded until existing events are processed.**
**(EE) **
**(EE) Backtrace:**
**(EE) 0: /usr/bin/X (xorg_backtrace+0x4e) [0x561990eb768e]**
**(EE) 1: /usr/bin/X (mieqEnqueue+0x253) [0x561990e99373]**
**(EE) 2: /usr/bin/X (QueuePointerEvents+0x52) [0x561990d73152]**
**(EE) 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f0ee2b8c000+0x60a7) [0x7f0ee2b920a7]**
**(EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f0ee2b8c000+0x687d) [0x7f0ee2b9287d]**
**(EE) 5: /usr/bin/X (0x561990d03000+0x96ac8) [0x561990d99ac8]**
**(EE) 6: /usr/bin/X (0x561990d03000+0xbfc92) [0x561990dc2c92]**
**(EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (0x7f0ee8b86000+0x352f0) [0x7f0ee8bbb2f0]**
**(EE) 8: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7f0ee3e1a000+0x56a20) [0x7f0ee3e70a20]**
**(EE) 9: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7f0ee3e1a000+0x5f9cf) [0x7f0ee3e799cf]**
**(EE) 10: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7f0ee3e1a000+0x56bd21) [0x7f0ee4385d21]**
**(EE) **
**(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.**
**(EE) [mi] mieq is *NOT* the cause. It is a victim.**

#3 It looks like it keeps trying to cycle between my graphics cards 3 outputs but i only have one vizio tv hooked up via hdmi. then reloads the login screen crashing seconds later. only happen when i let the computer idle for a long time 30mins to 3hours

> [ 2464.305] (II) XKB: reuse xkmfile /var/lib/xkb/server-DEBE90A2CC369F0AB28A88484F784DB1F2300F0E.xkm[ 2469.315] (--) NVIDIA(GPU-0): CRT-0: disconnected
[ 2469.315] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[ 2469.315] (--) NVIDIA(GPU-0): 
[ 2469.315] (--) NVIDIA(GPU-0): DFP-0: disconnected
[ 2469.315] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[ 2469.315] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[ 2469.315] (--) NVIDIA(GPU-0): 
[ 2469.343] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): connected
[ 2469.343] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): Internal TMDS
[ 2469.343] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): 340.0 MHz maximum pixel clock
[ 2469.343] (--) NVIDIA(GPU-0): 
[ 2469.344] (--) NVIDIA(GPU-0): CRT-0: disconnected
[ 2469.344] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[ 2469.344] (--) NVIDIA(GPU-0): 
[ 2469.344] (--) NVIDIA(GPU-0): DFP-0: disconnected
[ 2469.344] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[ 2469.344] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[ 2469.344] (--) NVIDIA(GPU-0): 
[ 2469.372] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): connected
[ 2469.372] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): Internal TMDS
[ 2469.372] (--) NVIDIA(GPU-0): VIZ E320i-A0 (DFP-1): 340.0 MHz maximum pixel clock
[ 2469.372] (--) NVIDIA(GPU-0):
[ 2469.891] (II) XKB: reuse xkmfile /var/lib/xkb/server-DEBE90A2CC369F0AB28A88484F784DB1F2300F0E.xkm

This was also in every Xorg log file I assume this is part of the 2 flashes on the login splash.

> [ **46.394] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event8)****[ 46.394] (II) No input driver specified, ignoring this device.**
**[ 46.394] (II) This device may have been added with another device file.**
**[ 46.394] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event9)**
**[ 46.394] (II) No input driver specified, ignoring this device.**
[ 46.394] (II) This device may have been added with another device file.
[ 46.394] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event4)
[ 46.394] (II) No input driver specified, ignoring this device.
[ 46.394] (II) This device may have been added with another device file.
[ 46.395] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[ 46.395] (II) No input driver specified, ignoring this device.
[ 46.395] (II) This device may have been added with another device file.
[ 46.395] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[ 46.395] (II) No input driver specified, ignoring this device.
[ 46.395] (II) This device may have been added with another device file.
[ 46.395] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event7)
[ 46.395] (II) No input driver specified, ignoring this device.
[ 46.395] (II) This device may have been added with another device file.
[ 46.396] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)

---

