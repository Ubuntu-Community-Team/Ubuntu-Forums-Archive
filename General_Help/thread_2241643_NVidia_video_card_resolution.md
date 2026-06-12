---
title: "NVidia video card resolution"
date: 2014-08-27
forum: General Help
---

### Post by ineuw on 2014-08-27
I would like configure my NVidia GeForce GT 620 video card to 1408 x 792 which is a valid 16:9 resolution. I used gksudo nvidia-settings and configured it through the X Server settings but it keeps reverting to 1280 x 720. In windows, there is no problem to configure the card to this resolution. Can anyone tell me the best way to do it?

---

### Post by ineuw on 2014-09-10
After doing some serious deep fishing on the web, I cobbled together the solution which works for me, and perhaps others who are stuck for lack of clear help. To add a resolution not listed in the X Server, the following steps were taken to gather the necessary information for appending a new resolution. My signature indicates the hardware and software.)

First, run "**xrandr**" without any options, to yield the monitor's name, which in this case is **"HDMI-0"**. It also lists the existing resolutions in descending order from optimal to minimal, and marks the current resolution with an asterisk. [*]

**ineuw@SANFRANCISCO:~$** xrandr
Screen 0: minimum 8 x 8, current 1280 x 720, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1280x720+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.0 +   60.0     60.0     59.9     30.0     24.0     60.1     60.0  
   1280x1024      60.0  
   1280x720       60.0*    59.9  
   1024x768       60.0  
   800x600        60.3  
   720x480        59.9  
   640x480        60.0     59.9  

then, navigate to the /etc/X11 folder.
**ineuw@SANFRANCISCO:~$** cd /etc/X11

then open the **xorg.conf** file for editing.
**ineuw@SANFRANCISCO:~$** sudo leafpad xorg.conf

and add the following Option line to the **"Device"** section as shown below.
Option "ModeValidation" "AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck,  AllowNonEdidModes, NoEdidMaxPClkCheck"

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "ModeValidation" "AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck,  AllowNonEdidModes, NoEdidMaxPClkCheck"
EndSection

**Save the file and log out and then log in - to be sure that the option was accepted.**

next run the **"cvt"** command with the desired resolution and refresh rate, which for LCD monitors is usually 60MHz.
**ineuw@SANFRANCISCO:/etc/X11$** cvt 1408 792 60

this returned the following values.

# 1408x792 59.93 Hz (CVT 1.12M9) hsync: 49.32 kHz; pclk: 90.75 MHz
Modeline "1408x792_60.00"   90.75  1408 1480 1624 1840  792 795 800 823 -hsync +vsync

the information needed for our next step was the second line with the word "Modeline" ommitted and noting for later that the resolution's name is: **"1408x792_60.00"**
**"1408x792_60.00"   90.75  1408 1480 1624 1840  792 795 800 823 -hsync +vsync**

append the result from **"cvt"** to **"xrandr --newmode"** and run.
**ineuw@SANFRANCISCO:/etc/X11$ **xrandr --newmode "1408x792_60.00"   90.75  1408 1480 1624 1840  792 795 800 823 -hsync +vsync

combine the monitor's name and the resolution name and append it to "xrandr --addmode" and run.
**ineuw@SANFRANCISCO:/etc/X11$** xrandr --addmode HDMI-0 "1408x792_60.00"

Open the Nvidia X Server Settings and you will find accepted resolutions never thought existed.

Note the modified "Screen section" 

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
[B]        Depth       24
        Modes      "1408x792" "1408x792"[/B]
    EndSubSection
EndSection

finally set output 
**ineuw@SANFRANCISCO:~$** xrandr --output HDMI-0 --mode "1408x792_60.00"


The correct resulting xorg.conf.doc is attached to the next post.

---

### Post by ineuw on 2014-09-10
Attached updated xorg.conf.doc file

---

