---
title: "945GM &amp; 24&quot; = 1920x1200 not working"
date: 2007-09-21
forum: General Help
---

### Post by OCP_001 on 2007-09-21
My system has the intel 945GM graphics controller and a 24" BenQ 241W LCD screen via DVI attached to it.

I got a display resolution of 1600x1200 after feisty was installed. "Screen resolution" had no higher settings available.  

Xorg.o.log shows "*(II) I810(0): Not using mode "1920x1200" (no mode of this name)*" -what does this mean? :confused:

Has anybody an idea how to get 1920x1200 working?

Below some interesting points in the xorg.0.log:
.
[I](**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "BenQ 241W"
(**) |   |-->Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
.
.
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found
.
.
II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (720,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: DFP (digital flat panel): attached: TRUE, present: TRUE, size: (1920,1200)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,1031)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,1031)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,1031)
(II) I810(0): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,1031)
(II) I810(0): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,1031)
(II) I810(0): Size of device DFP (digital flat panel) is 1920 x 1200
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	DFP (digital flat panel)
(II) I810(0): Lowest common panel size for pipe A is 1920 x 1200
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
.
.
(II) I810(0): Manufacturer: BNQ  Model: 76db
(II) I810(0): Year: 2006  Week: 50
(II) I810(0): EDID Version: 1.3
(II) I810(0): Digital Display Input
(II) I810(0): Max H-Image Size [cm]: horiz.: 52  vert.: 33
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.653 redY: 0.337   greenX: 0.295 greenY: 0.607
(II) I810(0): blueX: 0.144 blueY: 0.075   whiteX: 0.313 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): 1152x870@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) I810(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) I810(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) I810(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 154.0 MHz   Image Size:  519 x 324 mm
(II) I810(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) I810(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) I810(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) I810(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 83 kHz, PixClock max 170 MHz
(II) I810(0): Monitor name: BenQ 241W
.
.
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) I810(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) I810(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) I810(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) I810(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) I810(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) I810(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) I810(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) I810(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) I810(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  140.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  133.00  1280 1368 1504 1728  1024 1027 1034 1070 -hsync +vsync
(II) I810(0): Modeline "1600x1200"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
(II) I810(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
(II) I810(0): Modeline "1920x1200"  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync +vsync
(II) I810(0): Modeline "640x350"   25.17  640 656 752 800  350 387 389 449 -hsync +vsync
.
.
(II) I810(0): BenQ 241W: Using hsync range of 30.00-83.00 kHz
(II) I810(0): BenQ 241W: Using vrefresh range of 56.00-76.00 Hz
(II) I810(0): Not using mode "1920x1200" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1600 -> 2048).
(--) I810(0): Virtual size is 1600x1200 (pitch 2048)
(**) I810(0): *Built-in mode "1600x1200"
(**) I810(0):  Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(**) I810(0): Display dimensions: (520, 330) mm
(**) I810(0): DPI set to (78, 92)
.
.
[/I]

---

### Post by prince_niceguy on 2007-09-21
type the following in the terminal

sudo dpkg-reconfigure xserver-xorg

select the resolution you want, this option will start appearing in your selection.

---

### Post by OCP_001 on 2007-09-21
Nope, does not work.

The log is from my original xorg.conf, but I tried "sudo dpkg-reconfigure xserver-xorg" with the resolution set to 1920x1200 and different other settings (frambuffer on/off,display auto detection and manual settings for frequency and so on).

I also tried the alternative "intel" driver (even worse -only 1024x768 was available and a strange 1920x1920 could be selected in screen res, but did not work). Then tried the 915resolution. I did a search for 945 in this forum and tried every hint on that topic for the last two days -No success at all....

The interesting thing is that I had the same problem with OpenBSD, but not with opensuse 10.2. Suse had also 1600x1200 as maximum available, but there was a option for aspect ration. After changing from 4:3 to 16:10, 1920x1200 was available and working. I am missing such an option in the screen res tool. Maybe I have to reinstall suse and check the xorg.conf there, to get a hint what is missing :confused:
 
I expect nothing special, just to run my display in it's native resolution. Why is it that hard to get it working?

---

### Post by jclemmons on 2007-09-21
I had the same issue with an Intel chipset on a Dell system of mine that is attached to my HDTV.  I got around it by installing the intel driver out of the repositories.  You can do that by going to a terminal and typing:

sudo apt-get install xserver-xorg-video-intel

I'm not sure if that'll work for you, but it did for me.  The package "915resolution" is supposed to help with setting up extra resolutions for X, but I didn't have much luck with it.

---

### Post by mtb-cliff on 2007-09-21
I am having a similar problem with the intel 82865 driver and a 22" widescreen LCD. The 1680x1050 resolution displays a maximum of about 1440x1050, but the rest is accessible (kind of) in that if you know where the menu should be you can move your mouse off screen - can't see it though, and then click on the menu. If the menu is close enough to the edge of the displayed screen  then you can see it and select it - ex. System->Preferences->Screen Resolution, is visible but the System Menu is not. Looking through the /var/log/Xorg.0.log indicates that the driver is not selecting the required mode :

(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan

I was going to try building the intel driver to my kernel as someone else explained in a different forum. Haven't had time yet though.

I have tried the i810 driver, with and without the 915resolution hack, the new intel driver, all with and without the FB. No workies.

---

### Post by OCP_001 on 2007-09-22
Had no luck with comparing suse xorg.conf and the ubuntu one. 



I have surrendered to this problem...but there is light at the end of the tunnel! Did install 7.10 and viola!

1920x1200 was working without a problem!!! Maybe there is a bug in 7.04. 


The gibbon err... the dude minds :)

---

