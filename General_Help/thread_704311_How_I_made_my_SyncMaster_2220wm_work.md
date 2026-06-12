---
title: "How I made my SyncMaster 2220wm work"
date: 2008-02-22
forum: General Help
---

### Post by szquirrel on 2008-02-22
Yesterday I got a spanky new Samsung SyncMaster 2220wm monitor, and then I spent three hours tearing out my hair trying to get it to work. The worst part was trying to figure out the correct "Modeline" entry to put in /etc/X11/xorg.conf to get my monitor to display 1680x1050.

Finally I was reading /var/log/Xorg.0.log and I stumbled across these lines:
```
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 150 MHz

```
Well lookee here! Everything you need to build a proper modeline entry. To wit:
```
Modeline        "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
```

This was a breakthrough, but unfortunately it wasn't the end.

I had been running the latest, greatest ATI driver on my 9800 Pro, following the directions on the [ATI Linux Driver Wiki](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). I ran into two problems:
[LIST=1]
[*]My neat new Modeline entry was being entirely ignored. I finally solved this by commenting out **ALL** of the modeline entries, even the ones put there by the ATI driver setup. After doing this, the driver magically figured out that it could display 1680x1050.
[*]Even so, it still didn't work. I had vertical bars of corrupted junk running down the left and right sides of the screen. Maybe this is related to the "topic number 737-31720" problems when screen width is not a multiple of 64? I don't know, and at this point I was beyond caring.
[/LIST]

Ultimately I backed out the ATI proprietary "fglrx" driver and used the default "ati" driver. Once I cleaned up my xorg.conf and added the new modeline entry, everything worked fine. I doubt I'll be playing many 3D games in Ubuntu, but that's what Windows is for, right?

[grumble]Hand-editing dot clock rates into a conf file... WTF? is this 1997? Stupid linux bush-league hardware support.[/grumble]

---

### Post by wPwLUi3N on 2008-03-28
It is very irritating when hardware manufacture provide out of box support for vista but do not even support Linux (Very sad).

I am glad it worked out for you.

---

### Post by azimuth on 2008-03-28
I can sympathize with your plight. I brought home a SyncMaster 216 BW a couple of months ago and expected much the same as you got. I have a Radeon 9500 Pro and had already gone a few rounds with x.org configuration. I had already given up on  the restricted drivers and settled for the default driver with modest desktop effects.  I was really dreading a renewed battle, but couldn't resist the beautiful wide-screen monitor. Please don't hate me, but I had a plug-n-play experience.  Turned it on and it was there in the native 1680x1050 resolution.BLAM.! The kernel found the monitor and loaded everything it needed. It works well with the native Linux 3D games and I couldn't be happier. I am rather impressed with how well the Linux coders are doing without manufacturer support.

---

### Post by kezzel on 2008-05-15
szquirrel

THANKS.  I got a good deal on the 2220wm and had problems with the sync.

Here is what made mine work.  

```
Section "Module"
  Load         "glx"
  Load         "type1"
  Load         "extmod"
  Load         "dbe"
  Load         "freetype"
  Load         "dri"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "microsoftpro"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "Microsoft 3-Button Mouse with IntelliEye(TM)"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  Option       "CalcAlgorithm" "XServerPool"
  DisplaySize  720 270
  HorizSync    30-95
  Identifier   "Monitor[0]"
  ModelName    "MONITOR"
  Option       "DPMS"
  VendorName   "___"
  VertRefresh  50-160
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1680x1050" 157 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
EndSection


Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
#    Modes      "1280x1024" "1280x960" "1024x768" "800x600" "768x576" 
  EndSubSection
  SubSection "Display"
    Depth      16
#    Modes      "1280x1024" "1280x960" "1024x768" "800x600" "768x576" 
  EndSubSection
  SubSection "Display"
    Depth      24
#    Modes      "1280x1024" "1280x960" "1024x768" "800x600" "768x576" 
  EndSubSection
  SubSection "Display"
    Depth      8
#    Modes      "1280x1024" "1280x960" "1024x768" "800x600" "768x576" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "ATI RADEON 9600 Series (RV350/RV360 4152)"
  Driver       "fglrx"
  Identifier   "Device[0]"
  Option       "SaXDualHead"
  Option       "FSAADisableGamma" "no"
  Option       "CapabilitiesEx" "0x00000000"
  Option       "FSAAMSPosY0" "0.000000"
  Option       "FSAAMSPosX3" "0.000000"
  Option       "mtrr" "off"
  Option       "FSAAMSPosY1" "0.000000"
  Option       "FSAAMSPosX4" "0.000000"
  Option       "FSAAMSPosY2" "0.000000"
  Option       "ForceGenericCPU" "no"
  Option       "FSAAMSPosX5" "0.000000"
  Option       "FSAAScale" "1"
  Option       "FSAAMSPosY3" "0.000000"
  Option       "FSAAMSPosX0" "0.000000"
  Option       "GammaCorrectionI" "0x00000000"
  Option       "no_accel" "no"
  Option       "FSAAMSPosY4" "0.000000"
  Option       "FSAACustomizeMSPos" "no"
  Option       "UseFastTLS" "0"
  Option       "FSAAMSPosY5" "0.000000"
  Option       "FSAAEnable" "no"
  Option       "BlockSignalsOnLock" "on"
  Option       "GammaCorrectionII" "0x00000000"
  Option       "KernelModuleParm" "locked-userpages"
  Option       "Capabilities" "0x00000000"
  Option       "no_dri" "no"
  Option       "VideoOverlay" "on"
  Option       "PseudoColorVisuals" "off"
  Option       "StereoSyncEnable" "1"
  Option       "UseInternalAGPGART" "no"
  Option       "SaXDualMonitorVendor" "___"
  Option       "HSync2" "30-95"
  Option       "DesktopSetup" "Clone"
  Option       "SaXDualResolution" "1680x1050"
  Option       "SaXDualOrientation" "LeftOf"
  Option       "FSAAMSPosX1" "0.000000"
  Option       "SaXDualMode" "Clone"
  Option       "ForceMonitors" "auto,crt1"
  Option       "SaXDualHSync" "30-95"
  Option       "SaXDualMonitorModel" "MONITOR"
  Option       "SaXDualVSync" "50-160"
  Option       "VRefresh2" "50-160"
  Option       "Mode2" "1680x1050,1600x1024,1600x1000,1400x1050,1280x1024,1440x900,1280x960,1366x768,1280x800,1152x864,1280x768,1024x768,1280x600,1024x600,800x600,768x576,640x480"
  Option       "Stereo" "off"
  Option       "OpenGLOverlay" "off"
  Option       "FSAAMSPosX2" "0.000000"
  Option       "ScreenOverlap" "0"
  Option       "CenterMode" "off"
  Screen       0
  VendorName   "ATI"
EndSection
```


I changed the modeline from "1280x1024" to "1680x1050" and commented out the modes

---

