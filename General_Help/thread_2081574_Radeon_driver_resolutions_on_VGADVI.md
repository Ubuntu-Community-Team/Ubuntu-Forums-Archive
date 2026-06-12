---
title: "Radeon driver resolutions on VGA/DVI"
date: 2012-11-07
forum: General Help
---

### Post by axelmasok on 2012-11-07
Not one to give in and ask for help but I'm hoping for a lead here after too many hrs testing and reading.

HIS 4670 Card with HDMI/DVI/VGA
Samsung Monitor VGA/DVI only
Radeon open source driver

If using a HDMI to DVI cable EDID info is detected and I can choose the max resolution supported 1920x1080.

Remove the HDMI and boot with VGA only = 1024x768.  No EDID detected.  No problem, try and utilise the EDID info in a file (worked but not supported by Radeon driver without disabling KMS).

Try adding mode using xrandr = yes works but I can't see top and bottom of desktop and it won't stretch to full width of screen.

Try using the modeline copied from Xorg.conf on HDMI = same as the above xorg attempt.  

Something is missing here.  What is EDID providing that I need to put in xorg.conf?  Hor/Vert refresh I added = no diff.

DPI?  Have tried "DisplaySize 477 268" but still no diff.

I'm out of ideas...  Is there somewhere else I can post if not here? Cheers!

---

### Post by axelmasok on 2012-11-07
I've looked through this for hours.  Maybe someone else can point out the issue.  This is a snippet of Xorg.0.log with both monitors plugged in with VGA and HDMI.  I'm using the same modeline for VGA but it's not the same output on the screen!

```
[  6743.592] (II) RADEON(0): KMS Color Tiling: enabled
[  6743.592] (II) RADEON(0): KMS Pageflipping: enabled
[  6743.592] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  6743.605] (II) RADEON(0): Output VGA-0 using monitor section Monitor0
[  6743.638] (II) RADEON(0): Output HDMI-0 has no monitor sectio
[  6743.673] (II) RADEON(0): EDID for output VGA-0
[  6743.673] (II) RADEON(0): Printing probed modes for output VGA-0
[  6743.673] (II) RADEON(0): Modeline "1920x1080_VGA"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync +vsync (66.6 kHz)
[  6743.673] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6743.673] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6743.673] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  6743.673] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[  6743.673] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[  6743.706] (II) RADEON(0): EDID for output HDMI-0
[  6743.706] (II) RADEON(0): Manufacturer: SAM  Model: 49b  Serial#: 1129132594
[  6743.706] (II) RADEON(0): Year: 2009  Week: 1
[  6743.706] (II) RADEON(0): EDID Version: 1.3
[  6743.706] (II) RADEON(0): Digital Display Input
[  6743.706] (II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[  6743.706] (II) RADEON(0): Gamma: 2.20
[  6743.706] (II) RADEON(0): DPMS capabilities: Off
[  6743.706] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  6743.706] (II) RADEON(0): First detailed timing is preferred mode
[  6743.706] (II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
[  6743.706] (II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[  6743.706] (II) RADEON(0): Supported established timings:
[  6743.706] (II) RADEON(0): 720x400@70Hz
[  6743.706] (II) RADEON(0): 640x480@60Hz
[  6743.706] (II) RADEON(0): 640x480@67Hz
[  6743.706] (II) RADEON(0): 640x480@72Hz
[  6743.706] (II) RADEON(0): 640x480@75Hz
[  6743.706] (II) RADEON(0): 800x600@56Hz
[  6743.706] (II) RADEON(0): 800x600@60Hz
[  6743.706] (II) RADEON(0): 800x600@72Hz
[  6743.706] (II) RADEON(0): 800x600@75Hz
[  6743.706] (II) RADEON(0): 832x624@75Hz
[  6743.706] (II) RADEON(0): 1024x768@60Hz
[  6743.706] (II) RADEON(0): 1024x768@70Hz
[  6743.706] (II) RADEON(0): 1024x768@75Hz
[  6743.706] (II) RADEON(0): 1280x1024@75Hz
[  6743.706] (II) RADEON(0): Manufacturer's mask: 0
[  6743.706] (II) RADEON(0): Supported standard timings:
[  6743.706] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  6743.706] (II) RADEON(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[  6743.706] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[  6743.706] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  6743.706] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[  6743.706] (II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[  6743.707] (II) RADEON(0): Supported detailed timing:
[  6743.707] (II) RADEON(0): clock: 138.5 MHz   Image Size:  477 x 268 mm
[  6743.707] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[  6743.707] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[  6743.707] (II) RADEON(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 75 kHz, PixClock max 175 MHz
[  6743.707] (II) RADEON(0): Monitor name: SyncMaster
[  6743.707] (II) RADEON(0): Serial No: HMES100047
[  6743.707] (II) RADEON(0): EDID (in hex):
[  6743.707] (II) RADEON(0):    00ffffffffffff004c2d9b0432324d43
[  6743.707] (II) RADEON(0):    0113010380301b782a3d81a6564a9a24
[  6743.707] (II) RADEON(0):    125054bfef00714f8100814081809500
[  6743.707] (II) RADEON(0):    b300010101011a3680a070381f403020
[  6743.707] (II) RADEON(0):    3500dd0c1100001a000000fd00383d1e
[  6743.707] (II) RADEON(0):    4b11000a202020202020000000fc0053
[  6743.707] (II) RADEON(0):    796e634d61737465720a2020000000ff
[  6743.707] (II) RADEON(0):    00484d45533130303034370a20200049

[  6743.707] (II) RADEON(0): Printing probed modes for output HDMI-0
[  6743.707] (II) RADEON(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[  6743.707] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1680x945"x60.0  131.48  1680 1784 1960 2240  945 946 949 978 -hsync +vsync (58.7 kHz)
[  6743.707] (II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[  6743.707] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1366x768"x60.0   85.89  1366 1439 1583 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
[  6743.707] (II) RADEON(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1280x768"x60.0   68.25  1280 1328 1360 1440  768 771 778 790 +hsync -vsync (47.4 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6743.707] (II) RADEON(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[  6743.707] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  6743.707] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  6743.707] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  6743.707] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6743.707] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  6743.707] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[  6743.707] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[  6743.707] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  6743.707] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  6743.708] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  6743.708] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  6743.732] (II) RADEON(0): EDID for output DVI-0
[  6743.732] (II) RADEON(0): Output VGA-0 connected
[  6743.732] (II) RADEON(0): Output HDMI-0 connected
[  6743.732] (II) RADEON(0): Output DVI-0 disconnected
[  6743.732] (II) RADEON(0): Using exact sizes for initial modes
[  6743.732] (II) RADEON(0): Output VGA-0 using initial mode 1920x1080_VGA
[  6743.732] (II) RADEON(0): Output HDMI-0 using initial mode 1920x1080
[  6743.732] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  6743.732] (II) RADEON(0): mem size init: gart size :7dff000 vram size: s:40000000 visible:fcc0000
[  6743.732] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  6743.732] (==) RADEON(0): DPI set to (96, 96)

```

---

### Post by axelmasok on 2012-11-07
When I run xrandr I get the following output. Does anyone know what the mm measurements are in the output?  One is 0mm x0mm and the HDMI is something else.

```
axel@axel-K8T-Master2-FAR:~$ xrandr 
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080_VGA   59.9* 
   1024x768       60.0  
   800x600        60.3     56.2                                                                                                                                                                                                                                                
   848x480        60.0                                                                                                                                                                                                                                                         
   640x480        59.9                                                                                                                                                                                                                                                         
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm                                                                                                                                                                                        
   1920x1080      59.9*+                                                                                                                                                                                                                                                       
   1680x1050      59.9                                                                                                                                                                                                                                                         
   1680x945       60.0                                                                                                                                                                                                                                                         
   1400x1050      59.9                                                                                                                                                                                                                                                         
   1600x900       60.0                                                                                                                                                                                                                                                         
   1280x1024      75.0     60.0                                                                                                                                                                                                                                                
   1440x900       59.9                                                                                                                                                                                                                                                         
   1280x960       60.0                                                                                                                                                                                                                                                         
   1366x768       60.0                                                                                                                                                                                                                                                         
   1360x768       60.0                                                                                                                                                                                                                                                         
   1280x800       59.9                                                                                                                                                                                                                                                         
   1152x864       75.0                                                                                                                                                                                                                                                         
   1280x768       60.0                                                                                                                                                                                                                                                         
   1024x768       75.1     70.1     60.0                                                                                                                                                                                                                                       
   1024x576       60.0                                                                                                                                                                                                                                                         
   832x624        74.6                                                                                                                                                                                                                                                         
   800x600        72.2     75.0     60.3     56.2                                                                                                                                                                                                                              
   848x480        60.0                                                                                                                                                                                                                                                         
   640x480        72.8     75.0     66.7     60.0                                                                                                                                                                                                                              
   720x400        70.1                                                                                                                                                                                                                                                         
DVI-0 disconnected (normal left inverted right x axis y axis)
```

---

### Post by axelmasok on 2012-11-07
Solved.  tried a different monitor that had another VGA cable.  Somehow this magical VGA cable actually does pass EDID.  I have tried 3 other VGA cable previously and 2 DVI cables and have never been able to pass EDID.
So it's solved but really not completely solved in a way.

---

### Post by project_isaac on 2012-12-31
Sorry for posting to a solved thread, and you're probably not reading this anymore, but is there any chance that the "magic" VGA cable has 15 pins whilst the other ones had only 14 or less? I get a similar issue while using a cable that is missing pin 9 (5V power, presumably for the EDID rom), but when using a 15-pin vga cable, no issues with the horizontal squishing.

Interestingly, once the correct resolution has been set over the 15-pin vga, switching to the 14-pin vga without detecting monitors gives a correct resolution on said monitor. Still trying to figure out a way to fix (more accurately, workaround)  this on a software level.

---

