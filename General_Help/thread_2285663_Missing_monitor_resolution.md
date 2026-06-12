---
title: "Missing monitor resolution"
date: 2015-07-07
forum: General Help
---

### Post by tofiffe on 2015-07-07
I have a laptop with a GeForce 840M graphicscard and I've used the Additional Drivers tool to install proprietary tested drivers, but now even though my monitor supports 1920x1080, the maximum resolution I can set is [COLOR=#111111][FONT=Ubuntu]1366x768.

I've tried the following: 
[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]cvt 1920 1080[/FONT][/COLOR]
xrandr --newmode <modeline from the above command> [COLOR=#111111][FONT=Consolas]xrandr --addmode eDP1 1920x1080_60.00 #eDP1 is the used screen listed when I use xrandr -q[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

but this gives me the following error:
[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]X Error of failed request:  BadMatch (invalid parameter attributes)[/FONT][/COLOR]
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37 [COLOR=#111111][FONT=Consolas]  Current serial number in output stream:  38[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

Still an interesting thing is that this is listed among other devices when using xrandr -q:
[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
  1920x1080_60.00 (0x229)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz [COLOR=#111111][FONT=Consolas]        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

I don't have a monitors.xml file in my ~/.config folder, so I can't edit/check it.

How could I get at least 1920x1080 resolution to display in my settings?

UPDATE: aparently my system is using the integrated graphics card (seen under Settings->Details->Graphics) is there a way to switch it to NVidia?[/FONT][/COLOR]

---

### Post by efflandt on 2015-07-08
Which Ubuntu version and which nvidia drivers did you install? I don't know which nvidia driver the 840M might require, but on my desktop PC my GTX 750 Ti which was one of the first Nvidia cards with the new Maxwell chip did not work with **nvidia-current** package in Ubuntu 14.04, although, it worked with **nvidia-331-updates** package (which is what I use on my laptop with hybrid Intel HD 4600/Nvidia GTX 765M). Does your laptop have indication of which graphics is being used (my laptop power button is blue when using Intel and amber when using Nvidia)? You can see which nvidia package is installed by entering the following in a terminal window:```
dpkg-query -l nvidia* | grep ii
```If that is compatible with your Nvidia chip it would usually default to Nvidia graphics and **NVIDIA X Server Settings** would allow you to switch between Nvidia and Intel graphics. I have to log out of X and back in after switching from Nvidia to Intel, but have to reboot after switching Intel to Nvidia before it takes effect.

What is the native resolution of your laptop screen? When my laptop is using Intel graphics xrandr shows:```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```It is only slightly different while using Nvidia graphics:```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```Even if your screen is natively 1366x768 the closest that Linux video drivers get to that is 1360x768 (which works fine on such displays).

---

### Post by tofiffe on 2015-07-08
The laptop is new, it has a fresh install of Ubuntu Gnome 15.04, Gnome version is 3.14.2.

About the indicator, I don't think I have one to indicate whether the NVidia card is being used or not.

Command  results:
```
-$ dpkg-query -l nvidia* | grep iiii  nvidia-346              346.59-0ubuntu1  amd64        NVIDIA binary driver - version 346.59
ii  nvidia-opencl-icd-346   346.59-0ubuntu1  amd64        NVIDIA OpenCL ICD
ii  nvidia-settings         346.59-0ubuntu1  amd64        Tool for configuring the NVIDIA graphics driver



```

I've installed the drivers using the Additional drivers built in program, native resolution of the screen is 1920x1080, **NVIDIA X Server Settings** don't have the option to switch.

xrandr outputs the following:
```
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



```

---

### Post by gordintoronto on 2015-07-08
What is the brand and model of your laptop?

---

