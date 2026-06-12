---
title: "Xrandr Commands Not Working"
date: 2024-02-14
forum: General Help
---

### Post by ptmcompound on 2024-02-14
I've got an old Sony Bravia 32" television. The output from my machine via HDMI to it has a bad overscan issue. There is no option within the menu of the TV iteself to correct this. I've researched a lot on this and found a couple of xrandr commands to try:

```
xrandr --output HDMI-0 --set underscan on

```

```
xrandr --output HDMI-0 --set audio force-dvi --mode 1920x1080
```

I always get the below error when trying these:

```
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  29
  Current serial number in output stream:  29
```


Below are the xrandr and xrandr --verbose results for me.. Any help to resolve this is much appreciated. Thank you. 


Here is the xrandr output from terminal:

```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DVI-D-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 528mm x 297mm
   1920x1080     60.00*+  74.97    59.94    50.00  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1360x768      59.96 +
   1920x1080     60.05*   60.00  
   1296x720      59.42  
   1280x720      60.00    59.94  
   1248x768      59.87  
   1024x768      70.07    60.00  
   800x600       85.06    75.00    72.19    60.32    56.25  
   720x480       59.94  
   640x480       85.01    75.00    72.81    59.95    59.94  
  1080p (0xd15) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz
  1920 (0xd1a) 220.640MHz -HSync +VSync
        h: width  1920 start 2056 end 2264 total 2608 skew    0 clock  84.60KHz
        v: height 1080 start 1081 end 1084 total 1128           clock  75.00Hz
```



And the verbose:

```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DVI-D-0 connected primary 1920x1080+0+0 (0x1bc) normal (normal left inverted right x axis y axis) 528mm x 297mm
	Identifier: 0x1bb
	Timestamp:  1151182963
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	_MUTTER_PRESENTATION_OUTPUT: 0 
	CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
		0 1 
	CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
	EDID: 
		00ffffffffffff004c2d7d7051524130
		2e1f010380351e782adfd5a35b4da125
		0d5054bfef8081c0810081809500a9c0
		b300714f0101023a801871382d40582c
		450010292100001e000000fd00324b1e
		5412000a202020202020000000fc004c
		4632345433350a2020202020000000ff
		0048434e524231333735320a202001e6
		020313b146901f0413031267030c0010
		000024011d00bc52d01e20b828554010
		292100001e8c0ad090204031200c4055
		001029210000188c0ad08a20e02d1010
		3e9600102921000018011d007251d01e
		206e28550010292100001e2a4480a070
		3827403020350010292100001a000000
		00000000000000000000000000000020
	BorderDimensions: 4 
		supported: 4
	Border: 0 0 0 0 
		range: (0, 65535)
	SignalFormat: TMDS 
		supported: TMDS
	ConnectorType: DVI-D 
	ConnectorNumber: 0 
	_ConnectorLocation: 0 
	non-desktop: 0 
		supported: 0, 1
  1920x1080 (0x1bc) 148.500MHz +HSync +VSync *current +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x1bd) 174.500MHz +HSync -VSync
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock  83.89KHz
        v: height 1080 start 1083 end 1088 total 1119           clock  74.97Hz
  1920x1080 (0x1be) 148.350MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1920x1080 (0x1bf) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1680x1050 (0x1c0) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1600x900 (0x1c1) 108.000MHz +HSync +VSync
        h: width  1600 start 1624 end 1704 total 1800 skew    0 clock  60.00KHz
        v: height  900 start  901 end  904 total 1000           clock  60.00Hz
  1440x900 (0x1c2) 106.500MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1280x1024 (0x1c3) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1280x1024 (0x1c4) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x800 (0x1c5) 83.500MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock  49.70KHz
        v: height  800 start  803 end  809 total  831           clock  59.81Hz
  1280x720 (0x1c6) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x1c7) 74.180MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1280x720 (0x1c8) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1152x864 (0x1c9) 108.000MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
        v: height  864 start  865 end  868 total  900           clock  75.00Hz
  1024x768 (0x1ca) 78.750MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
        v: height  768 start  769 end  772 total  800           clock  75.03Hz
  1024x768 (0x1cb) 75.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
        v: height  768 start  771 end  777 total  806           clock  70.07Hz
  1024x768 (0x1cc) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x1cd) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x1ce) 50.000MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock  48.08KHz
        v: height  600 start  637 end  643 total  666           clock  72.19Hz
  800x600 (0x1cf) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x1d0) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  720x576 (0x1d1) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0x1d2) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x1d3) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x1d4) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  696 total  832 skew    0 clock  37.86KHz
        v: height  480 start  481 end  484 total  520           clock  72.81Hz
  640x480 (0x1d5) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
HDMI-0 connected 1920x1080+0+0 (0x1d8) normal (normal left inverted right x axis y axis) 708mm x 398mm
	Identifier: 0x1d6
	Timestamp:  1151182963
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	_MUTTER_PRESENTATION_OUTPUT: 0 
	CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
		0 1 
	CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
	EDID: 
		00ffffffffffff004dd9012501010101
		0111010380472878ee000400544c0026
		0f50542fcc0031404540614081c0314f
		454f31594559201c50a0500016303020
		350047280000001a201c00c050003130
		4020070443280010001a000000fc0053
		4f4e592054560a2020202020000000fd
		000a55013908000a2020202020200120
		02031774448405030223090707830100
		0065030c001000011d107251d01e206e
		285500e8121100001e011d8018711c16
		20582c2500c48e2100009e8c0ad08a20
		e02d10103e9600c48e210000188c0ad0
		8a20e02d10103e9600138e2100001800
		00000000000000000000000000000000
		0000000000000000000000000000008f
	BorderDimensions: 4 
		supported: 4
	Border: 0 0 0 0 
		range: (0, 65535)
	SignalFormat: TMDS 
		supported: TMDS
	ConnectorType: HDMI 
	ConnectorNumber: 1 
	_ConnectorLocation: 1 
	non-desktop: 0 
		supported: 0, 1
  1360x768 (0x1d7) 72.000MHz +HSync -VSync +preferred
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock  47.37KHz
        v: height  768 start  771 end  776 total  790           clock  59.96Hz
  1920x1080 (0x1d8) 74.250MHz +HSync +VSync Interlace *current
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1124           clock  60.05Hz
  1920x1080 (0x1d9) 74.180MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
        v: height 1080 start 1084 end 1094 total 1124           clock  60.00Hz
  1296x720 (0x1da) 74.250MHz +HSync +VSync
        h: width  1296 start 1406 end 1446 total 1666 skew    0 clock  44.57KHz
        v: height  720 start  725 end  730 total  750           clock  59.42Hz
  1280x720 (0x1c6) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x1c7) 74.180MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1248x768 (0x1db) 72.000MHz +HSync -VSync
        h: width  1248 start 1312 end 1344 total 1472 skew    0 clock  48.91KHz
        v: height  768 start  784 end  791 total  817           clock  59.87Hz
  1024x768 (0x1cb) 75.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
        v: height  768 start  771 end  777 total  806           clock  70.07Hz
  1024x768 (0x1cc) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x1dc) 56.250MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock  53.67KHz
        v: height  600 start  601 end  604 total  631           clock  85.06Hz
  800x600 (0x1cd) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x1ce) 50.000MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock  48.08KHz
        v: height  600 start  637 end  643 total  666           clock  72.19Hz
  800x600 (0x1cf) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x1d0) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  720x480 (0x1d2) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x1dd) 36.000MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock  43.27KHz
        v: height  480 start  481 end  484 total  509           clock  85.01Hz
  640x480 (0x1d3) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x1d4) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  696 total  832 skew    0 clock  37.86KHz
        v: height  480 start  481 end  484 total  520           clock  72.81Hz
  640x480 (0x1de) 25.180MHz -HSync -VSync
        h: width   640 start  648 end  744 total  800 skew    0 clock  31.48KHz
        v: height  480 start  482 end  484 total  525           clock  59.95Hz
  640x480 (0x1d5) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  1080p (0xd15) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz
  1920 (0xd1a) 220.640MHz -HSync +VSync
        h: width  1920 start 2056 end 2264 total 2608 skew    0 clock  84.60KHz
        v: height 1080 start 1081 end 1084 total 1128           clock  75.00Hz
```

---

### Post by TheFu on 2024-02-15
Please wrap terminal output in forum code tags, so columns line up. Too hard to read otherwise.

xrandr is for X11 (xorg), not Wayland.  Are you 100% certain you **are not** running Wayland as the display server on your computer?
```
echo $XDG_SESSION_TYPE
```
should provide that answer.

*--set audio* isn't listed as a valid option in the manpage here for 20.04 or 22.04.  Are you certain that's allowed?

---

### Post by ptmcompound on 2024-02-16
> **TheFu said:**
> Please wrap terminal output in forum code tags, so columns line up. Too hard to read otherwise.

xrandr is for X11 (xorg), not Wayland.  Are you 100% certain you **are not** running Wayland as the display server on your computer?
```
echo $XDG_SESSION_TYPE
```
should provide that answer.

*--set audio* isn't listed as a valid option in the manpage here for 20.04 or 22.04.  Are you certain that's allowed?


Appreciate your reply, but I've just purchased a decent, newer used TV on FB Marketplace. My TV was very old, and from everything I read, it's just easier if you have the option on the TV itself. My new TV has the 'Full Pixel' option for the Display Area setting, and this does the trick. I now can see the entire output of my computer to TV with no overscan. Easier solution and avoids any further headache dealing with this issue on the OS side.

---

### Post by Holger_Gehrke on 2024-02-17
@TheFu: --set is a 'per-output' option that's part of xrandr since version 1.2. It sets values for properties which can be listed with 'xrandr --properties'. Whether or not 'audio' is a valid property and 'force-dvi' is a valid value for that property depends on the connected display. On my system 'audio' is valid for a display connected by HDMI that has a headphone jack but will only take the values 'on', 'off', and 'auto'. According to the verbose output ptmcompound posted, there is no 'audio' property for this display ('xrandr --verbose' will list properties too).

Holger

---

