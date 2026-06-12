---
title: "Issue with Second Display Monitor (Unknown Display) and Missing 1600x900 Resolution"
date: 2023-05-11
forum: General Help
---

### Post by mksundaram2 on 2023-05-11
Hello Ubuntu Community,


I am facing an issue with my second display monitor on Ubuntu, and I'm seeking assistance to resolve it. Here are the details of my problem:


1. Hardware Configuration:
   - Graphics Card: AMD/ATI Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
   - Monitor: Connected via VGA, supports 1600x900 resolution


2. Problem Description:
   - The second display monitor is recognized as "Unknown Display" in Ubuntu.
   - The available resolutions for the second display are limited to 1024x768, 848x480, and 800x600.
   - The desired resolution of 1600x900 is not available for the second display.


3. Dual Boot Setup:
   - I have a dual boot configuration with Windows 7 and Ubuntu.
   - In Windows 7, the second display monitor works fine and supports the 1600x900 resolution without any issues.


I have already tried the following steps to resolve the issue, based on suggestions received earlier:


- Installed the "xserver-xorg-video-radeon" package.
- Used the "xrandr" command to add a new mode for 1600x900 resolution.
- Checked for additional drivers using the "Additional Drivers" tool, but no suitable driver was found.


Despite these efforts, the issue persists, and I'm unable to set the desired resolution for my second display monitor on Ubuntu.


I kindly request the Ubuntu community's assistance in resolving this issue. If you have any suggestions, insights, or possible solutions, I would greatly appreciate your guidance.


Thank you in advance for your help!

---

### Post by MAFoElffen on 2023-05-11
Please run the [UbuntuForums 'system-info' script]("https://ubuntuforums.org/showthread.php?t=2475932") and Post the URL of the pastebin the report uploads to.

It has an extensive Graphics section that will tell us your hardware, settings and what it see's from Linux. We will then review it and come up with recommendations for a solution.

---

### Post by mksundaram2 on 2023-05-12
[https://paste.ubuntu.com/p/yDcsbJqfxv/](https://paste.ubuntu.com/p/yDcsbJqfxv/)

---

### Post by MAFoElffen on 2023-05-12
At the Graphical Login screen, after you select the user, use the gear icon on the lower right to select Xorg, instead of Wayland... Does the resolution work then?

---

### Post by Holger_Gehrke on 2023-05-12
You might want to try to read the EDID (extended display ID). The package read-edid contains get-edid and parse-edid which you call like this:
```

sudo get-edid|parse-edid

```
This should give you all the information both of your displays give your PC about themselves. If your second display isn't shown in the output then either the VGA cable doesn't have all pins connected - specifically it would be missing three pins for the Display Data Channel - or the VGA connector on your graphics card doesn't implement DDC.

Holger

---

### Post by MAFoElffen on 2023-05-12
I'm thinking it is having a problem reading the EDID with Wayland, which is sometimes a problem with Wayland. 

After changing to Xorg, rerun
```

xrandr -q

```
FYI -- 'get-edit' and 'parse-edid' commands are part of package 'read-edid' which would have to be installed. Not a default installed package...

---

### Post by mksundaram2 on 2023-05-13
I tried your suggestion, still the resolution doesn't change, I mean the problem of the unknown display and the resolution 1600x900 is missing.

---

### Post by mksundaram2 on 2023-05-13
this is the output: 
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
Problem requesting slave address: Device or resource busy
No EDID on bus 1
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
No EDID on bus 8
No EDID on bus 9
No EDID on bus 10
No EDID on bus 11
No EDID on bus 12
No EDID on bus 13
No EDID on bus 14
1 potential busses found: 2
256-byte EDID successfully retrieved from i2c bus 2
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
	Identifier "SA240Y"
	ModelName "SA240Y"
	VendorName "ACR"
	# Monitor Manufactured week 18 of 2021
	# EDID version 1.3
	# Analog Display
	DisplaySize 530 300
	Gamma 2.20
	Option "DPMS" "true"
	Horizsync 31-75
	VertRefresh 56-75
	# Maximum pixel clock is 180MHz
	#Not giving standard mode: 1152x864, 75Hz
	#Not giving standard mode: 1280x1024, 60Hz
	#Not giving standard mode: 1280x720, 60Hz
	#Not giving standard mode: 1280x800, 60Hz
	#Not giving standard mode: 1440x900, 60Hz
	#Not giving standard mode: 1680x1050, 60Hz
	#Not giving standard mode: 1920x1080, 60Hz
	Modeline 	"Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
EndSection

The acer monitor is reflected, but my lg monitor is not shown here.

---

### Post by MAFoElffen on 2023-05-13
Is the LG also not seen by xrandr? And which display is connected to the DVI and HDMI?

---

### Post by MAFoElffen on 2023-05-13
If not seen by 
```

xrandr -q --verbose

```
But is seen by 
```

xrandr --listmonitors

```
Then I think I know what is going on... 

I asked the questions about what display is connected to what port on that Radeon card in my last post (unanswered)... That Radeon card has 3 ports= HDMI, DVI, and VGA. I am assuming that the primary display is connected to the HDMI and the secondary display is connected to the DVI port, through a DVI to HDMI cable or adapter of the same...
> 
Display Data Channel (DDC)
Main article: Display Data Channel

The Display Data Channel (DDC) is a communication channel based on the I2C bus specification. HDMI specifically requires the device implement the Enhanced Display Data Channel (E-DDC), which is used by the HDMI source device to read the E-EDID data from the HDMI sink device to learn what audio/video formats it can take.[5]:&#8202;§§8.1,CEC-1.2&#8211;CEC-1.3&#8202; HDMI requires that the E-DDC implement I2C standard mode speed (100 kbit/s) and allows it to optionally implement fast mode speed (400 kbit/s).[5]:&#8202;§4.2.8&#8202;

The DDC channel is actively used for High-bandwidth Digital Content Protection (HDCP). 
DVI ports are missing those two channels, (in the conversion from HDMI), so the card cannot get the EDID of the display.

Two ways around that...

Option #1: One way is to use xrandr to define and add the new mode to the port. This is not persistent. So would have to be added to ~/.xinitrc file to add the mode after User login... Or define and add from an xorg.conf file.

This link explains how to add a new mode, via those two different methods: [https://ubuntuforums.org/showthread.php?t=1743535&p=10907238#post10907238](https://ubuntuforums.org/showthread.php?t=1743535&p=10907238#post10907238)

Option #2: Use 'get-edid' to extract the EDID to a raw file saved somewhere on the system, so you can include it in an xorg.conf file. You can do this by temporarily connecting the display via the HDMI port, to extract the EDID... That way the system sees "all" the modes the LG display can do natively. Better, cleaner solution.

The following two links should explain how to do that--
RE: 
[https://manpages.ubuntu.com/manpages/jammy/man1/get-edid.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/get-edid.1.html)
[https://ubuntuforums.org/showthread.php?t=1743535&p=10925558#post10925558](https://ubuntuforums.org/showthread.php?t=1743535&p=10925558#post10925558)

That Graphics Resolution Sticky has been there for almost 12 years now, and this is why it is still there and still relevant. (LOL)

---

### Post by mksundaram2 on 2023-05-14
I am using onboard, Intel, vga to acer and radeon graphic card vga to lg. I tried lg with onboard Intel, still the result was same.
As the HDMI port is not working, that's why I am using vga to connect both the monitors.
Note:- My LG monitor does shows 1600x900 resolution in windows 7. So the problem is with Ubuntu OS.

---

### Post by mksundaram2 on 2023-05-14
this is the output:
sundaram@mks:~$ xrandr -q
Screen 0: minimum 16 x 16, current 2944 x 1204, maximum 32767 x 32767
XWAYLAND0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      59.92*+
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77  
XWAYLAND1 connected 1920x1080+1024+124 (normal left inverted right x axis y axis) 530mm x 300mm
   1920x1080     59.96*+
   1440x1080     59.99  
   1400x1050     59.98  
   1280x1024     59.89  
   1280x960      59.94  
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   1680x1050     59.95  
   1440x900      59.89  
   1280x800      59.81  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   1600x900      59.95  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77  
sundaram@mks:~$ 

ZWAYLAND0 is my LG Monitor, I assume, and XWAYLAND1 is my Acer Monitor. I don't see 1600x900 resolution in XWAYLAND0 and one more thing on display settings it only has three option to select from they are: 1024x768, 848x480 and 800x600 only.

---

### Post by mksundaram2 on 2023-05-17
am I missing something, If so kindly let me know. As I don't see any replies to my last post. Thanks

---

### Post by MAFoElffen on 2023-05-17
I didn't see your post from 3 days ago, and I am busy making changes and improvements to the UbuntuForums 'system-info' script... My apologies for your wait... (Besides, this is volunteer work, because i like to help. Not a job.)

I asked you to change your login to Xorg XServer to try. I can see by the Port Names (YWAYLAND, XWAYLAND) that you are still using Wayland... You will not be able to add a resolution mode or use a Custom EDID unless you are using Xorg. Wayland does not have the facility for that. Besides, you were asked to try Xorg, to see if it recognized anything different, right?

*I'll wait... Until you change and retest that.*

---

### Post by mksundaram2 on 2023-05-18
I sincerely apologize if my previous post unintentionally conveyed any disrespect towards the selfless work you do. I deeply appreciate and admire your dedication and contributions to the community.

I would change to Xorg and post the result of the same. Thanks

---

### Post by MAFoElffen on 2023-05-18
I think option #1 from post #10 is what will help you. It assumes that either you can't get a clean EDID table to dump to a file, or that it just doesn't matter and you are going to set to a mode anyways...

You might try option #2, just to see if you can offload the LG's EDID table from it, but if it doesn't, then there is no need to do that. 

There is a Windows version of that type of the EDID tool that is GUI, that might be able to connect to your LG display. I have used it. It is one that was recommended to me by nVidia for dumping EDID tables to files, via Windows OS: 
[https://www.entechtaiwan.com/util/moninfo.shtm](https://www.entechtaiwan.com/util/moninfo.shtm)

If using Xorg, then I use the Xorg.0.log file:
```

grep '(II) modeset(G0):' /var/log/Xorg.0.log

```
...and look at the info the GPU see's when it queries the attached display's  EDID table.

---

### Post by MAFoElffen on 2023-05-18
Most will tell you that you can "only" use Xorg to change the resolution manually... And to be able to use xrandr or xorg.conf to change it. And that it won't work with Wayland...

That is the official accepted answer... But you can change things in Wayland via the dbus API... I have tested and used this script, which adds xrandr type of functionality, while using Wayland... If you are set on using Wayland, then I'll share the link to you. It's still a use at your own risk disclaimer.
RE: [https://gitlab.com/Oschowa/gnome-randr](https://gitlab.com/Oschowa/gnome-randr)

Download. Make it executable.

Test to see what it sees
```

./gnome-randr.py

```
Set to a (found) mode via a (found) port...
```

./gnome-randr.py --output VGA-1 --rotate normal --mode 1600x900

```
I don't know if it can add a mode that is "not there" (like xrandr)... I don't see the Python code to implement that in the script code.

Otherwise, with xrandr
```

xrandr --newmode Modeline "1600x900"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr --addmode VGA-1 1600x900
xrandr --output VGA-1 --mode 1600x900 -rate 60

```
If that works, then add to a file ~/.xinitrc or create an /etc/X11/xorg.conf file to add that mode in it, and use it...

---

### Post by mksundaram2 on 2023-05-18
```
The result of post #10 Option 1:


sundaram@mks:~$ xrandr -q --verbose
Screen 0: minimum 320 x 200, current 2624 x 900, maximum 16384 x 16384
HDMI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x52
    Timestamp:  119890
    Subpixel:   horizontal rgb
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    TearFree: auto 
        supported: off, on, auto
    output_csc: bypass 
        supported: bypass, tvrgb, ycbcr601, ycbcr709
    audio: auto 
        supported: off, on, auto
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    dither: off 
        supported: off, on
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: off, on, auto
    coherent: 1 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 50 
        supported: 50
    non-desktop: 0 
        range: (0, 1)
DVI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x53
    Timestamp:  119890
    Subpixel:   horizontal rgb
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    TearFree: auto 
        supported: off, on, auto
    output_csc: bypass 
        supported: bypass, tvrgb, ycbcr601, ycbcr709
    audio: auto 
        supported: off, on, auto
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    dither: off 
        supported: off, on
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: off, on, auto
    coherent: 1 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 52 
        supported: 52
    non-desktop: 0 
        range: (0, 1)
VGA-1 connected primary 1024x768+0+0 (0x56) normal (normal left inverted right x axis y axis) 0mm x 0mm
    Identifier: 0x54
    Timestamp:  119890
    Subpixel:   no subpixels
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    _MUTTER_PRESENTATION_OUTPUT: 0 
    TearFree: auto 
        supported: off, on, auto
    output_csc: bypass 
        supported: bypass, tvrgb, ycbcr601, ycbcr709
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    load detection: 1 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 54 
        supported: 54
    non-desktop: 0 
        range: (0, 1)
  1024x768 (0x56) 65.000MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x57) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x58) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  848x480 (0x59) 33.750MHz +HSync +VSync
        h: width   848 start  864 end  976 total 1088 skew    0 clock  31.02KHz
        v: height  480 start  486 end  494 total  517           clock  60.00Hz
  640x480 (0x5a) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
VGA-1-1 connected 1600x900+1024+0 (0x7d) normal (normal left inverted right x axis y axis) 527mm x 296mm
    Identifier: 0x7b
    Timestamp:  119801
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       4
    CRTCs:      4 5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    _MUTTER_PRESENTATION_OUTPUT: 0 
    EDID: 
        00ffffffffffff0004727f053d4a8011
        121f010368351e78ee0565a756529c27
        0f5054b30c00714f818081c081009500
        b300d1c00101023a801871382d40582c
        45000f282100001e000000fd00384b1f
        4b12000a202020202020000000fc0053
        41323430590a202020202020000000ff
        005439325349303032323433300a005b
    PRIME Synchronization: 0 
        supported: 0, 1
    link-status: Good 
        supported: Good, Bad
    CTM: 420160213 1 390610691 -2147483648 68657360 -2147483648 4394435 0 -7568605 0 12152591 0 51151133 0 163963301 0 
        -202741000 0 
    CONNECTOR_ID: 61 
        supported: 61
    non-desktop: 0 
        range: (0, 1)
  1600x900_60.00 (0x7d) 118.250MHz -HSync +VSync *current +preferred
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock  55.99KHz
        v: height  900 start  903 end  908 total  934           clock  59.95Hz
  1920x1080 (0x7e) 148.500MHz +HSync +VSync +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1680x1050 (0x7f) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1280x1024 (0x80) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1440x900 (0x81) 106.500MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1280x800 (0x82) 83.500MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock  49.70KHz
        v: height  800 start  803 end  809 total  831           clock  59.81Hz
  1152x864 (0x83) 108.000MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
        v: height  864 start  865 end  868 total  900           clock  75.00Hz
  1280x720 (0x84) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1024x768 (0x85) 75.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
        v: height  768 start  771 end  777 total  806           clock  70.07Hz
  1024x768 (0x56) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x57) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x58) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x86) 30.240MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock  35.00KHz
        v: height  480 start  483 end  486 total  525           clock  66.67Hz
  640x480 (0x5a) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  720x400 (0x87) 28.320MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
        v: height  400 start  412 end  414 total  449           clock  70.08Hz
  1024x768 (0x56) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x57) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x58) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x5a) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
sundaram@mks:~$ 




The result of post #10 Option 2:
sundaram@mks:~$ xrandr --listmonitors
Monitors: 2
 0: +*VGA-1 1024/271x768/203+0+0  VGA-1
 1: +VGA-1-1 1600/527x900/296+1024+0  VGA-1-1
sundaram@mks:~$
```

---

### Post by MAFoElffen on 2023-05-18
VGA-1-1 is your Acer display and it's EDID table is being seen. VGA-1 is your LG display, and it's EDID table is not being seen.

Before you do anything else, let's keep you out of trouble with the Moderators here... This Forum's policy is that User's wrap all comands and Raw output with CODE Tags. Please go back to your last post, selct "Edit Post" > "Advanced" ... Then selct the text of the output with your muse, to highlight it. Then select the "#" Icon from the editor menu. That will wrap all that is selected with CODE Tags. Save the edit. 

Now go to Post #17 and try the 'xrandr' commands and see if they work for you...

---

### Post by mksundaram2 on 2023-05-19
From post #5
[COLOR=#000000]This should give you all the information both of your displays give your PC about themselves. If your second display isn't shown in the output then either the VGA cable doesn't have all pins connected - specifically it would be missing three pins for the Display Data Channel - or the VGA connector on your graphics card doesn't implement DDC.

I swapped the vga cables and now LG Monitor is shown and acer is shown as unknown display and more over the LG now has 1600x900 and acer, unknow display, has maximum 1600x900. it should have 1920x1080 or more.

So I feel there must be issue with the vga cable. I would change it and revert. Thanks[/COLOR]

---

