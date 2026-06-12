---
title: "Is it possible to change the refresh rate in 13.04?"
date: 2013-05-06
forum: General Help
---

### Post by Naygral on 2013-05-06
**The question: **Is it possible to change the refresh rate in Lubuntu 13.04; and if so, how?

I have been troubled by some terrible screen tearing for some time, on all *buntu distros I have tested (except for Lubuntu 12.04, for some odd reason). I was able to fix this on Ubuntu by installing Compiz Config Settings and changing the refresh rate to 60. But I guess that this may not be the most optimal way of fixing it on Lubuntu, because of "Compiz" is used to handle more performance intense graphics, something that I do not want on a computer that are supposed to be more lightweight.

So I am pretty sure that this problem is about the refresh rate, and I do now wonder how I could explicitly tell Lubuntu that 60 is the preferred refresh rate, because it seems as it does not have a clue! :P

---

### Post by papibe on 2013-05-06
Hi Naygral.

Could you post the results of these commands?
```
lspci -nnk | grep -iA2 vga

xrandr -q

xrandr -q --q1

xvidtune -show
```
Regards.

---

### Post by Naygral on 2013-05-06
> **papibe said:**
> Hi Naygral.

Could you post the results of these commands?
```
lspci -nnk | grep -iA2 vga

xrandr -q

xrandr -q --q1

xvidtune -show
```
Regards.

[B]lspci -nnk | grep -iA2 vga:
[/B]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G71 [GeForce 7900 GTX] [10de:0290] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:0343]
    Kernel driver in use: nvidia

[B]xrandr -q:
[/B]Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 4096 x 4096
DVI-I-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0  
   1152x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)


[B]xrandr -q --q1:
[/B]SZ:    Pixels          Physical       Refresh
*0   1920 x 1080   ( 530mm x 291mm )  *50  
 1   1680 x 1050   ( 463mm x 283mm )   51  
 2   1600 x 900    ( 441mm x 243mm )   52  
 3   1280 x 1024   ( 353mm x 276mm )   53   54  
 4   1280 x 960    ( 353mm x 259mm )   55  
 5   1280 x 720    ( 353mm x 194mm )   56  
 6   1152 x 720    ( 318mm x 194mm )   57  
 7   1024 x 768    ( 282mm x 207mm )   58   59  
 8    800 x 600    ( 220mm x 162mm )   60   61  
 9    640 x 480    ( 176mm x 129mm )   62   63  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis

[B]xvidtune -show:
[/B]"1920x1080"   148.50   1920 2008 2052 2200   1080 1084 1089 1125 +hsync +vsync

Thank you for any help you can provide!

---

### Post by papibe on 2013-05-06
Thanks.

Have you try setting on 'Sync to VBlank'?

If not, open 'Nvidia X Server Settings', go to 'OpenGL Settings' on the right, and then check that option on the left.

Let us know how it goes.
Regards.

---

### Post by Naygral on 2013-05-06
> **papibe said:**
> Thanks.

Have you try setting on 'Sync to VBlank'?

If not, open 'Nvidia X Server Settings', go to 'OpenGL Settings' on the right, and then check that option on the left.

Let us know how it goes.
Regards.

The setting was already checked, but I tried to uncheck it - restart the computer - and checked it again; and it seems to have fixed the problem!
I will bump this topic if the problem returns so I can ask for further assistance. But for now, thank you very much for the help you provided and the solution to the problem! ^^

---

