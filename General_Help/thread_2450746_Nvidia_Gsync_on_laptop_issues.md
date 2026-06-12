---
title: "Nvidia Gsync on laptop issues"
date: 2020-09-20
forum: General Help
---

### Post by getut on 2020-09-20
I have bought a new gaming laptop and it's the first one I've had with a Gsync capable display although I have been running Nvidia laptops under linux for many many years. I just can't get Gsync fully working.

It appears like the majority of the options that everyone talks about everywhere I have search don't show up on a laptop with Prime display. Only on full desktop varieties. So, I have tried everything and seem to have adaptive vsync partially working but I can't get fullscreen games to go full vsync with flipping instead of blit.

My laptop is an eluktronics with the 240hz gsync display and the Nvidia RTX 2080 Super Max Q and I've tried all the below with Ubuntu 20.04 as well as Mint 20. I'm using 450.66 nvidia drivers from the bleeding edge PPA.

I typically run cinnamon as my DE but after much research, I saw where mutter cannot be completely bypassed and the Gsync is impossible when running cinnamon even if you disable effects. So I added xubuntu-desktop meta package to my machine and started doing my testing in XFCE with compositing completely disabled. Even there Nvidia control panel kept showing synchronization: Off on the Display config page. I finally got it to show that turned on by adding nvidia-drm.modeset=1 to my grub config. That is the setting that got me closest and made a noticeable improvement is display quality when gaming.

What concerns me is my nvidia control panel shows no option to enable Gsync anywhere and there are so many tutorials out there of various ages that it is tough to tell WHERE I'm supposed to be seeing the option when using a Prime laptop. Some examples show it under the X Server Display Configuration page, but that appears to only be possible when its a full desktop card. WIth Prime mode enabled, this is what I see.. notice the synchronization: on down at the bottom. The grub setting is what got that going. But what concerns me is that even under OpenGL settings I have no option for GSync and under X Server XVideo Settings I show "Currently synced to display: Uknown". Any help getting Gsync fully working would be greatly appreciated.
[ATTACH=CONFIG]286992[/ATTACH][ATTACH=CONFIG]286993[/ATTACH][ATTACH=CONFIG]286994[/ATTACH]

---

### Post by getut on 2020-09-24
I am oh so close to 100% success. I have G-Sync working but I cannot get the 2nd monitor enabled with my configuration. Yes, I realize G-Sync won't work with the 2nd monitor on, but I can make a script that kills it as part of running any game that will be using G-Sync full screen.

Here is my full setup:
Eluktronics Max-17 laptop with RTX-2080 Super Max-Q. This laptop has a 240Hz G-Sync display on it. I have a 2nd NON G-Sync capable Dell monitor. Either Ubuntu 20.04 or Mint 20

Per the above questions, here is ALL of the things I had to change from the stock config to get G-Sync working even though I can't get the 2nd monitor to function correctly now. I was primarily using Cinnamon as my Desktop Environment. 

1) I had to edit the grub config to add the line nvidia-drm.modeset=1. See this thread. It is in reference to 18.04 but worked for my Ubuntu 20.04/Mint 20 install... [https://askubuntu.com/questions/1048274/ubuntu-18-04-stopped-working-with-nvidia-drivers](https://askubuntu.com/questions/1048274/ubuntu-18-04-stopped-working-with-nvidia-drivers)
2) In my BIOS config, this laptop has an option for the video chipset. I can run Intel only, Nvidia only or Hybrid (Nvidia Prime). I had to switch to Nividia only to even get the GSync options to be visible in the Nvidia X Server Settings Almost every tutorial or write up out there shows directions and screenshots for Desktop PC Nvidia cards under linux. The Nvidia X Server settings looks drastically different than all the screenshots you will see when your system is in Prime/Optimus/Hybrid mode. **_I can find no evidence anywhere that anyone has gotten G-Sync to work while in Hybrid mode._**
3) I had to ditch Cinnamon. G-Sync would not run with Cinnamon. Per docs that I found, even though full screen apps can disable effects in Cinnamon, it still routes it through Mutter which kills Gsync. I did not find this out until I found the magic in number 4 and 5 below, but I think those were specific to the problems down there. You won't have to do that if you have a monitor that is reporting it's g-sync capability correctly. But I ended up going with XFCE (installing xubuntu-desktop package) and then disabling composting completely in it's settings.

The above two settings should be enough for MOST machines. But just my luck, the 240 Hz G-sync capable display that comes with my Eluktronics Max-17 laptop either does not report it's G-Sync capability to the drivers properly, or the 450.66 Nvidia drivers are not detecting it properly. So my Nvidia X Settings was STILL not offering the G-Sync options to me on the OpenGL Settings tab, and I was still not getting a "Allow G-Sync on monitor not validated as G_sync compatible on the Display config tab. So continue with number 4  below. Up until this point both my monitors are still working because the system is still running off of xrandr.

3) To get my system to allow G-Sync with the screen not reporting correctly I found no way around having to configure my system directly via xorg configs. This has the side effect of making the system much less "portable". The config is hard coded and can't easily switch between home mode and travel mode where I don't have my 2nd monitor. The magic was putting in an xorg config that has the option UseEdid false. This made the system show me the G-Sync options when the monitor was no longer reporting incorrectly.

And here is where I stand. I have G_Sync working but NOTHING I do will get my 2nd monitor to activate. EIther it doesn't come on at all or it complains about an unsupported refresh rate. I am guessing when I do get it to try and enable the 2nd monitor, it is somehow trying to run it at 240hz vs 60hz.  I have even run an edid decode and built the monitors file with the output of it's edid info. But it still won't run. Also the displays app in XFCE will not let me enable the monitor and the resolution and refresh rate drop downs are completely empty.

So I'm close but still need some help.

Also... I did NOT do the things I have done so far in xorg.conf in /etc/X11    In an attempt to keep some level of flexibility in config, I did them in /usr/share/X11/xorg.conf.d in a newly created 10.monitors.conf file. It is posted below in case any part of it helps someone at least get to the point I am at. But as stated, I still need help with the Dell on HDMI-0. I'm gonig to open another thread specific to the xorg 2nd monitor activation problem since I technically have G-Sync working now. It will probably be a little less dizzying for anyone helping with that issue not to have to read through the G-Sync journey. I'll point back to this thread though.

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "DP-4"
    VendorName     "Unknown"
    ModelName      "AU Optronics Corporation"
    HorizSync       266.6 - 266.6
    VertRefresh     60.1 - 240.0
    Option         "DPMS"
    Option         "UseEdid" "false"
        Modeline        "Mode 0" 533.28 1920 1968 2000 2000 1080 1090 1095 1111 -hsync -vsync
        Modeline        "Mode 1" 533.28 1920 1968 2000 2000 1080 1090 1095 4440 -hsync -vsync
EndSection

Section "Monitor"
        Identifier "HDMI-0"
        ModelName "DELL U2414H"
        VendorName "DEL"
        DisplaySize 530 300
        Option "DPMS" "true"
        Horizsync 30-83
        VertRefresh 56-76
        # Maximum pixel clock is 170MHz
        #Not giving standard mode: 1152x864, 75Hz
        #Not giving standard mode: 1280x1024, 60Hz
        #Not giving standard mode: 1600x900, 60Hz
        #Not giving standard mode: 1600x1200, 60Hz
        #Not giving standard mode: 1920x1080, 60Hz

        #Extension block found. Parsing...
        Modeline        "Mode 13" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 2" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
        Modeline        "Mode 3" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
        Modeline        "Mode 4" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
        Modeline        "Mode 5" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
        Modeline        "Mode 6" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
        Modeline        "Mode 7" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
        Modeline        "Mode 8" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
        Modeline        "Mode 9" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
        Modeline        "Mode 10" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
        Modeline        "Mode 11" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
        Modeline        "Mode 12" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
        Modeline        "Mode 14" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
        Modeline        "Mode 15" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
        Modeline        "Mode 16" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync
        Option "PreferredMode" "Mode 13"
        Option "RightOf" "DP-4"
        Option "Position" "1920 0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "nvidia"
    Monitor        "DP-4"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DP-4: 1920x1080_240 +0+0 {AllowGSYNCCompatible=On}, HDMI-0: 1920x1080_60 +1920+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

