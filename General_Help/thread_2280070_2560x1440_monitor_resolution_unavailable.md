---
title: "2560x1440 monitor resolution unavailable"
date: 2015-05-27
forum: General Help
---

### Post by ***J*** on 2015-05-27
I am trying to set my monitor's resolution to 2560 x 1440, but the highest option available to me in nvidia x server settings is 1920 x 1080. What can I do to get a higher resolution? My specs:

Monitor: Acer K272HUL bmiidp 27-inch [http://us.acer.com/ac/en/US/content/model/UM.HX2AA.001](http://us.acer.com/ac/en/US/content/model/UM.HX2AA.001)
Graphics Card: EVGA GeForce GTX 550 Ti FPB [http://www.evga.com/articles/00618/](http://www.evga.com/articles/00618/) [http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-550ti/specifications](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-550ti/specifications)
Driver: NVIDIA binary driver - version 331.113 from nvidia-331-updates (proprietary)
Cable: KabelDirekt Mini HDMI to HDMI Cable [http://www.amazon.com/gp/product/B00DI89EQ2/](http://www.amazon.com/gp/product/B00DI89EQ2/)
OS: Ubuntu 14.04 LTS

---

### Post by ***J*** on 2015-05-28
output of xrandr:
```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 600mm x 340mm
   1920x1080      60.0*+   59.9     50.0     50.0     60.1     60.0     50.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       75.0     59.9  
   1280x1024      75.0     60.0  
   1280x720       60.0     59.9     50.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9     59.9  
DVI-I-3 disconnected (normal left inverted right x axis y axis)



```

---

### Post by Topsiho on 2015-05-28
according to [http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-550ti](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-550ti) the maximum resolution for this graphics card is 1680 x 1050.

Topsiho

---

### Post by Rexroni on 2015-05-28
I'm fighting a similar problem.  I got the correct output from this link:

[https://wiki.archlinux.org/index.php/Xrandr#Troubleshooting](https://wiki.archlinux.org/index.php/Xrandr#Troubleshooting)

Basically, using 
```
cvt <width in pixels> <height in pixels>
```
to get the format, which I fed into 
```
xrandr --newmode <format>
```
then
```
xrandr --output <name of the output> --addmode <name of the new mode>
```
then
```
xrandr --output <name of the output> --mode <name of the output>
```

Let me know if this works.  Also, let me know if your screen looks decent afterwards.  Mine was never quite as sharp as it was supposed to be... maybe I have that maximum resolution problem.

---

### Post by ***J*** on 2015-05-28
Hi thank you for your replies. Before I saw them I had tried a DVI cable I had lying around and that gave me the option to select 2560x1440 as a resolution.

After looking at my card on [http://www.gpuzoo.com/GPU-NVIDIA/GeForce_GTX_550_Ti.html](http://www.gpuzoo.com/GPU-NVIDIA/GeForce_GTX_550_Ti.html) I saw that the maximum DVI resolution is 2560 x 1600, while the maximum HDMI resolution is 1920 x 1200. I assumed I could get higher through HDMI, especially since it doesn't differentiate between the two for the maximum resolution specs on my graphic card's website and my HDMI cable is supposed to allow for 4K.

---

