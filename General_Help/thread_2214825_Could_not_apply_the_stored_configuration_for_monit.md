---
title: "Could not apply the stored configuration for monitors"
date: 2014-04-03
forum: General Help
---

### Post by hojjat on 2014-04-03
I have two monitors connected to my Ubuntu 12.04 machine. I recently upgraded my RAM, and ever since, Ubuntu has trouble using a suitable resolution for my monitors.

Basically, when I get to the login screen, the resolution is 640x480. After I log in, I can go to "Displays..." setting, uncheck "Mirror displays", and set the resolution of one of my monitors to 1920x1080. But for the other one, the only option I have is 640x480. Also, right after I login, I get the following error dialog: "Could not apply the stored configuration for monitors" (screenshot is below).

[IMG]http://i61.tinypic.com/1w576.png[/IMG]

The monitor for which only 640x480 is available is my DisplayPort-0. When I run xrandr I get:

```

DisplayPort-0 connected 640x480+0+600 (normal left inverted right x axis y axis) 510mm x 287mm
   640x480        60.0* 
   720x400        70.1  
DisplayPort-1 connected 1920x1080+640+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```

I can manually add the Modeline back for that monitor:

```

sudo xrandr --addmode DisplayPort-0 "1920x1080"

```

Then a 1920x1080 option will become available for that monitor in the "Displays..." setting. When I chose that option, the display changes to the suitable resolution without any problems. But, when I log off and log back in, the whole story happens again! That 1920x1080 resolution is not available again, and the displays are mirror again.

I tried *rm ~/.config/monitors.xml* but that didn't help either. Somehow, it seems that X is removing that modeline every time it starts.

Pertinent parts of my Xorg.0.log are pasted below

```

[144331.296] (II) RADEON(0): EDID for output DisplayPort-0
[144331.296] (II) RADEON(0): Manufacturer: DEL  Model: f035  Serial#: 1111111111
[144331.296] (II) RADEON(0): Year: 2011  Week: 48
[144331.296] (II) RADEON(0): EDID Version: 1.3
[144331.296] (II) RADEON(0): Digital Display Input
[144331.296] (II) RADEON(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[144331.296] (II) RADEON(0): Gamma: 2.20
[144331.296] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[144331.296] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[144331.296] (II) RADEON(0): First detailed timing is preferred mode
[144331.296] (II) RADEON(0): redX: 0.625 redY: 0.349   greenX: 0.339 greenY: 0.623
[144331.296] (II) RADEON(0): blueX: 0.153 blueY: 0.052   whiteX: 0.313 whiteY: 0.329
[144331.296] (II) RADEON(0): Supported established timings:
[144331.296] (II) RADEON(0): 720x400@70Hz
[144331.296] (II) RADEON(0): 640x480@60Hz
[144331.296] (II) RADEON(0): 640x480@75Hz
[144331.296] (II) RADEON(0): 800x600@60Hz
[144331.296] (II) RADEON(0): 800x600@75Hz
[144331.296] (II) RADEON(0): 1024x768@60Hz
[144331.296] (II) RADEON(0): 1024x768@75Hz
[144331.296] (II) RADEON(0): 1280x1024@75Hz
[144331.296] (II) RADEON(0): Manufacturer's mask: 0
[144331.296] (II) RADEON(0): Supported standard timings:
[144331.296] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[144331.296] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[144331.296] (II) RADEON(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[144331.296] (II) RADEON(0): Supported detailed timing:
[144331.296] (II) RADEON(0): clock: 148.5 MHz   Image Size:  510 x 287 mm
[144331.296] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[144331.296] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[144331.296] (II) RADEON(0): Serial No: VVVVVVVVVVVV
[144331.296] (II) RADEON(0): Monitor name: DELL E2311H
[144331.296] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[144331.296] (II) RADEON(0): EDID (in hex):
[144331.296] (II) RADEON(0):    00ffffffffffff0010ac35f04c334343
[144331.296] (II) RADEON(0):    3015010380331d78ea1e55a059569f27
[144331.296] (II) RADEON(0):    0d5054a54b00714f8180d1c001010101
[144331.296] (II) RADEON(0):    010101010101023a801871382d40582c
[144331.296] (II) RADEON(0):    4500fe1f1100001e000000ff00565856
[144331.296] (II) RADEON(0):    343931424f4343334c0a000000fc0044
[144331.296] (II) RADEON(0):    454c4c204532333131480a20000000fd
[144331.296] (II) RADEON(0): EDID vendor "DEL", prod id 61493
[144331.296] (II) RADEON(0): Using hsync ranges from config file
[144331.296] (II) RADEON(0): Using vrefresh ranges from config file
[144331.296] (II) RADEON(0): Printing DDC gathered Modelines:
[144331.296] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[144331.296] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[144331.296] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[144331.296] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[144331.296] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[144331.296] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[144331.296] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[144331.296] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[144331.296] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[144331.296] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[144331.296] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[144331.296] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[144331.296] (II) RADEON(0): Not using mode "1920x1080" (hsync out of range)
[144331.296] (II) RADEON(0): Not using mode "1280x1024" (vrefresh out of range)
[144331.296] (II) RADEON(0): Not using mode "1280x1024" (hsync out of range)
[144331.296] (II) RADEON(0): Not using mode "1152x864" (vrefresh out of range)
[144331.296] (II) RADEON(0): Not using mode "1024x768" (vrefresh out of range)
[144331.296] (II) RADEON(0): Not using mode "1024x768" (hsync out of range)
[144331.296] (II) RADEON(0): Not using mode "800x600" (vrefresh out of range)
[144331.296] (II) RADEON(0): Not using mode "800x600" (hsync out of range)
[144331.296] (II) RADEON(0): Not using mode "640x480" (vrefresh out of range)
[144331.296] (II) RADEON(0): Printing probed modes for output DisplayPort-0
[144331.296] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[144331.296] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[144331.356] (II) RADEON(0): EDID for output DisplayPort-1
[144331.356] (II) RADEON(0): Manufacturer: DEL  Model: 4061  Serial#: 111111112
[144331.356] (II) RADEON(0): Year: 2010  Week: 23
[144331.356] (II) RADEON(0): EDID Version: 1.3
[144331.356] (II) RADEON(0): Digital Display Input
[144331.356] (II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[144331.356] (II) RADEON(0): Gamma: 2.20
[144331.356] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[144331.356] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[144331.356] (II) RADEON(0): First detailed timing is preferred mode
[144331.356] (II) RADEON(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[144331.356] (II) RADEON(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[144331.356] (II) RADEON(0): Supported established timings:
[144331.356] (II) RADEON(0): 720x400@70Hz
[144331.356] (II) RADEON(0): 640x480@60Hz
[144331.356] (II) RADEON(0): 640x480@75Hz
[144331.356] (II) RADEON(0): 800x600@60Hz
[144331.356] (II) RADEON(0): 800x600@75Hz
[144331.356] (II) RADEON(0): 1024x768@60Hz
[144331.356] (II) RADEON(0): 1024x768@75Hz
[144331.356] (II) RADEON(0): 1280x1024@75Hz
[144331.356] (II) RADEON(0): Manufacturer's mask: 0
[144331.356] (II) RADEON(0): Supported standard timings:
[144331.356] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[144331.356] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[144331.356] (II) RADEON(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[144331.356] (II) RADEON(0): Supported detailed timing:
[144331.356] (II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[144331.356] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[144331.356] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[144331.356] (II) RADEON(0): Serial No: TTTTTTTTTTTT
[144331.356] (II) RADEON(0): Monitor name: DELL P2211H
[144331.356] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[144331.356] (II) RADEON(0): EDID (in hex):
[144331.356] (II) RADEON(0):    00ffffffffffff0010ac61404c323941
[144331.356] (II) RADEON(0):    1714010380301b78ea9535a159579f27
[144331.356] (II) RADEON(0):    0e5054a54b00714f8180d1c001010101
[144331.356] (II) RADEON(0):    010101010101023a801871382d40582c
[144331.356] (II) RADEON(0):    4500dd0c1100001e000000ff00545958
[144331.356] (II) RADEON(0):    44393036414139324c0a000000fc0044
[144331.356] (II) RADEON(0):    454c4c205032323131480a20000000fd
[144331.356] (II) RADEON(0):    00384c1e5311000a20202020202000ef
[144331.356] (II) RADEON(0): Printing probed modes for output DisplayPort-1
[144331.356] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[144331.356] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[144331.356] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[144331.356] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[144331.356] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[144331.356] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[144331.356] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[144331.356] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[144331.356] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[144331.356] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[144331.356] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[144331.356] (II) RADEON(0): Output DisplayPort-0 connected
[144331.356] (II) RADEON(0): Output DisplayPort-1 connected

```

How can I prevent X from forgetting/deleting the high resolution modeline? Any advice is highly appreciated.

---

### Post by hojjat on 2014-04-03
It is fixed now. I follow the instructions here: [http://gangmax.me/blog/2012/06/20/ubuntu-12-dot-04-login-screen-resolution-problem/](http://gangmax.me/blog/2012/06/20/ubuntu-12-dot-04-login-screen-resolution-problem/)

That did NOT fix the problem. Instead, once I restarted the computer Ubuntu complained about low-resolution graphic settings, and asked me to reconfigure graphics. I said yes, and that fixed the issue.

---

