---
title: "xrandr issue after upgrade to 20.04"
date: 2020-09-27
forum: General Help
---

### Post by stromek on 2020-09-27
I just upgraded to Ubuntu 20.04.01 and now my monitor resolution option isn't working

My laptop screen died some time ago so I started using it mirrored with an external monitor. The laptop uses a 4:3 screen, so I configured a 16:9 resolution option following these instructions: [http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)

It worked, though always a little goofy. I would pick the 16:9 in display settings and click "apply", then the test screen would show me the original 4:3 so if i clicked "revert settings" it would go to 16:9. sometimes it took a few tries, and I always had to do it after rebooting. But when I upgraded, it will not work at all. I pick the 16:9 and click apply. It shows me the 4:3 screen still, but whether i pick "revert" or "keep changes" it stays at 4:3. The other option in Display settings is a lower resolution 4:3 and that does work.

This is what the last 2 lines of the .profile file look like

xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr --addmode eDP1 "1600x900_60.00"



Any insights or just wild ideas to try would be much appreciated. :)

---

### Post by NM5TF on 2020-09-28
@stromek...

when you followed the xrandr instructions from the referenced web page, did you insert your OWN values or just copy/paste from web page ???
[COLOR="#FF0000"]is your display really labeled eDP1[/COLOR]...the same as in example ???

when you did the xrandr "newmode" & "addmode" commands did you get any errors ???

it would help if you posted the output of 
```
xrandr
```

it is also helpful if you post the command outputs in "code tags"....use the [COLOR="#FF0000"]adv reply [/COLOR]button, select the # character from menu, insert 
your values between the #s....it helps to stand out from background...like this...
```
[tommy@tommy ~]$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 4096 x 4096
VGA-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 370mm x 230mm
   1440x900      59.90*+
   1280x1024     60.02  
   1280x960      60.00  
   1366x768      59.79  
   1360x768      60.02  
   1280x800      74.93    59.91  
   1152x864      75.00  
   1280x768      74.89    59.99  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   1024x576      59.93  
   800x600       72.19    75.00    60.32    56.25  
   848x480       60.00  
   640x480       75.00    72.81    59.94  
   720x400       70.08  

```

tommy

---

### Post by ajgreeny on 2020-09-28
There is a thread at [https://ubuntuforums.org/showthread.php?t=2450912&p=13988638#post13988638](https://ubuntuforums.org/showthread.php?t=2450912&p=13988638#post13988638) which, though not about quite the same problem, may be helpful to you.

There are commands shown which could help you add resolution modelines if needed.

---

### Post by stromek on 2020-09-28
Yes i used the instructions with my own values. 

```
person@ad:~$ xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
eDP1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 170mm
   1600x900      60.01 +  59.82  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1368x768      60.00    59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.81    59.91  
   1152x864      60.00  
   1280x720      59.86    60.00    59.74  
   1024x768      60.00* 
   1024x576      60.00    59.90    59.82  
   960x540       60.00    59.63    59.82  
   800x600       60.32    56.25  
   864x486       60.00    59.92    59.57  
   800x450       60.00  
   640x480       59.94  
   720x405       59.51    60.00    58.99  
   640x360       59.84    59.32    60.00  
   1600x900_60.00  59.95  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   1600x900_60.00  59.95  
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
person@ad:~$ cvt 1600 900
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync


```

Well I thought i'd just try it all over again, mostly because i couldn't remember about any errors since i originally set it up probably 6  or 8 months ago. Add lo and behold an error indeed. 

```
person@ad:~$ sudo xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
[sudo] password for person: 
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  41
  Current serial number in output stream:  41


```

This sort of rings a bell from before too, but how did i fix it? no idea.
I checked out the other thread @ajgreeny suggested and here's my driver info, but i don't know what any next steps would be...the weird thing is it USED to work (more or less). ugh.

```
person@ad:~$ inxi -G
Graphics:
  Device-1: Intel Haswell-ULT Integrated Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.8 driver: i915 
  resolution: 1024x768~60Hz, 1024x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4400 (HSW GT2) 
  v: 4.5 Mesa 20.0.8
```


thanks for taking the time to help!

---

### Post by NM5TF on 2020-09-29
@stromek...

the output of xrandr shows your graphics card is capable of 1600x900 resolution, but something is forcing it to 1024x768....
you might try forcing the kernel to load the generic nouveau driver instead of the Intel i915 driver it is using now...
I had a similar problem when Nvidia dropped support for my legacy graphics card, changing the driver to nouveau fixed it...

you will need to edit the kernel parameters to load nouveau....if you don't know how to do that, go here...

[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

you will add nouveau to the end of the line starting with linux.....then reboot to see if you can now see the new resolution...
if it works, you will need to make it permanent following the 2nd part of instructions on the web page referenced above...

good luck

tommy

---

