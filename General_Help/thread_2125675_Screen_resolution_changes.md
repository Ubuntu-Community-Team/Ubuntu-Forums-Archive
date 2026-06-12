---
title: "Screen resolution changes"
date: 2013-03-14
forum: General Help
---

### Post by killiekosmos on 2013-03-14
I had 11.04 running fine on PC with monitor but I decided to use an old TV instead.  I connected it via VGA but got 640 x320 resolution with no option to change settings.  I reconnected old monitor and changed resolution to 1200 x 800 (?) and then swapped connections to TV "on the fly" and it worked!  However on reboot it has reverted to old settings with no option to change.

What can I do to resolve this?

Thanks

---

### Post by matt_symes on 2013-03-16
Hi

Boot into the PC with the monitor connected and change the resolution to the desired resolution for the TV.

Type the command

```
xvidtune -show
```

This will give you the mode line for the current resolution.

Here's an example

```

matthew-S206:/home/matthew % xvidtune -show
"1366x768"     69.30   1366 1414 1446 1462    768  770  775  790 -hsync -vsync

matthew-S206:/home/matthew % 
```

You show then be able to add the new mode when connected to the TV so connect the tv up and use xrandr.

First add the mode using xrandr --newmode with the values from the xvidtune command above.

Here's an example

```
xrandr --newmode "1366x768" 69.30   1366 1414 1446 1462    768  770  775  790 -hsync -vsync
```

Then add the mode using xrandr --addmode. Here's an example. make sure you specify the correct port, (VGA) in the example below, on which the TV is connected. You can find the correct port using xrandr with no parameters.

This is an example of xrandr with no parameters.

```
matthew-S206:/home/matthew % xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
matthew-S206:/home/matthew % 

```

You may be connected to HDMI ?

```
xrandr --addmode VGA 1366x768
```

Finally select the new mode. Once again this is an example.

```
xrandr --output VGA --mode 1366x768
```

If this works then we need to make it permenant.

Kind regards

---

