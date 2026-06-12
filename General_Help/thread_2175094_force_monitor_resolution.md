---
title: "force monitor resolution?"
date: 2013-09-17
forum: General Help
---

### Post by garyed on 2013-09-17
My preferred monitor resolution is 1280x1024 & it usually defaults to that every time I boot up in either 10.04 or 12.04. 
Sometimes something happens to my monitor & Ubuntu doesn't recognize it correctly. When that happens I only have a choice of 1024x768 or 800x600 which doesn't work very well. I can shut down completely & reboot but it still does the same thing. If I boot into windows I get the correct resolution & if I boot into Puppy linux even though it doesn't recognize the monitor it gives me a choice to set it correctly & then it works fine. So Ubuntu is where I need to be able to force it to accept that resolution. Does anyone know how to do that?

---

### Post by papibe on 2013-09-17
Hi garyed.

How the monitor is connected to the PC? What kind of cable? If it is through a VGA cable, are you able to use HDMI?

Could you post the results of these commands?
```
lspci -nnk | grep -iA2 vga

xrandr

xrandr -q --q1

xvidtune --show
```
Regards.

---

### Post by garyed on 2013-09-17
I'm pretty sure its just a standard vga cable. It's been working fine for a few years with Ubuntu 10.04 and about a year with 12.04. A couple months ago it started acting up & then it booted up one day fine. It's been fine ever since until today. Now I can't get the resolution back. I'm pretty sure there's something in the monitor that is not telling Ubuntu what it is that is causing the problem because it says "unknown monitor". Here's my outputs from those commands:> 
 lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5200] [10de:0322] (rev a1)
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
------------------------------------------------------------------
 xrandr
Screen 0: minimum 320 x 200, current 2304 x 1053, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-I-1 connected 1280x1024+1024+29 (normal left inverted right x axis y axis) 357mm x 268mm
   1280x1024      85.0 +   75.0* 
   1920x1440      60.0  
   1600x1200      75.0  
   1152x864       75.0  
   1024x768       85.0     75.1     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     66.7     60.0  
   720x400        87.8     70.1  
TV-1 disconnected (normal left inverted right x axis y axis)
--------------------------------------------------
 xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 610mm x 279mm )  *60  
 1    800 x 600    ( 610mm x 279mm )   60   56  
 2    848 x 480    ( 610mm x 279mm )   60  
 3    640 x 480    ( 610mm x 279mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis
----------------------------------------------------
xvidtune --show
Usage: xvidtune [option]
    where option is one of:
        -show                             Print current modeline to stdout
        -next                             Switch to next video mode
        -prev                             Switch to previous video mode
        -unlock                           Enable mode switch hot-keys
        -timeout [seconds]                Set testmode timeout in seconds,




---

### Post by papibe on 2013-09-17
Thanks.

It looks like there are more higher resolution when you use a DVI cable:
```
DVI-I-1 connected 1280x1024+1024+29 (normal left inverted right x axis y axis) 357mm x 268mm
1280x1024 85.0 + 75.0*
1920x1440 60.0
1600x1200 75.0
...
```
Is that another monitor?

Also, try get the output of this command when you are able to get into 1280x1024:
```
xvidtune -show
```
(only one dash)

Regards.

---

### Post by garyed on 2013-09-17
Thanks for taking the time to help,

> 
xvidtune -show
"1024x768"     65.00   1024 1048 1184 1344    768  771  777  806 -hsync -vsync



I do have a second monitor I use for my music recording program in Windows hooked up to the dvi output. Its the only program where i use dual monitors so it doesn't get turned on when I'm using Ubuntu. I could try to swap the plugs but since the resolution is fine in Windows the plug should work in Ubuntu too. I can also get the resolution I need running Puppy Linux
so there's something confined to Ubuntu that is not letting me get 1280x1024 out of the monitor the way it is now.

---

### Post by garyed on 2013-09-17
Well I disconnected the power from the system & monitor for about 6 hours & now it booted back up fine again. The resolution shows 1280x1024 & also it recognizes the brand & model of my monitor now. I think the problem is twofold. 
1- something with my monitor not sending the proper signal. 
2- something with Ubuntu that needs to see that signal from my monitor to get the resolution right.
I say that because Windows & Puppy Linux would still work fine with the monitor while Ubuntu 10.04 & 12.04 would not. 
I sure would like to find a way to force Ubuntu to use 1280x1024 no matter what monitor it sees because this is happened before & will probably happen again.

---

### Post by papibe on 2013-09-18
A couple of thoughts:

Now that your monitor is working again, you may obtain some data and hardcode into the xorg config file to "force" it when reading your monitor resolution.

You could:
[LIST]
[*]Get the proper modeline using xvidtune and add it to config file. Examples [here]("http://wiki.openelec.tv/index.php?title=Configuring_a_Custom_xorg.conf") and [here]("http://ubuntuforums.org/showthread.php?t=1480033").
[*]Or get the current monitor's EDID information into a file and force to use it every time. Example [here]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid"). Try using the tool get-edid from the 'read-edid' package.
[/LIST]
Let us know if you need more help with that.
Regards.

---

### Post by garyed on 2013-11-07
This thread is getting old but I still have not found a solution. 

I may go for a week or two without any problems but once I lose my resolution I can't get it back. If I shut the system down & cut the power to everything over night it usually fixes it but if i only do it for a couple of hours it does not. I've tried different xorg settings unsuccessfully so if anyone knows a solution please post it in depth because nothing has worked so far.

One more thing is that I can also boot into an old version of Ubuntu 7.10 & the resolution is fine so the problem seems to be only with versions that did not use an xorg file. This last time I lost my resolution right after using dosbox & have not been able to get it back. It acts like there is something Ubuntu is looking for from my monitor & not getting it right.

---

