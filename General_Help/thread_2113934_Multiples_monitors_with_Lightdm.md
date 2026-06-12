---
title: "Multiples monitors with Lightdm"
date: 2013-02-08
forum: General Help
---

### Post by GameX2 on 2013-02-08
Hi,

I've been trying to fix the LightDM wrong screen resolution on my 2 monitors (One laptop - LVSD1 and a VGA - VGA1 screen).
I've checked there:
[http://askubuntu.com/questions/119843/how-to-force-multiple-monitors-correct-resolutions-for-lightdm](http://askubuntu.com/questions/119843/how-to-force-multiple-monitors-correct-resolutions-for-lightdm)

I have the exact same problem.
Using the provided script fix the problem, that's great.

There's one last thing I would like to fix; I've used the script at the bottom of the page:

```
#!/bin/bash  XCOM0=`xrandr -q | grep 'VGA1 connected'`
XCOM1=`xrandr --output LVDS1 --primary --auto --output VGA1 --auto --right-of LVDS1`
XCOM2=`xrandr --output LVDS1 --primary --auto`
# if the external monitor is connected, then we tell XRANDR to set up an extended desktop
if [ -n "$XCOM0" ] || [ ! "$XCOM0" = "" ]; then echo $XCOM1
# if the external monitor is disconnected, then we tell XRANDR to output only to the laptop screen
else echo $XCOM2 fi  exit 0;
```It work great, although I would appreciate to show the login prompt on the VGA1 screen, and not the LVDS1 (laptop) screen.  Currently, I have the login prompt on my laptop, and only a Ubuntu logo on my VGA screen.  How can I make it the reverse?

Next, I would like to simply disable the display of my laptop on LightDM, when the VGA screen is connected.
The problem (Minor) is that when I login, the screen flash - because the laptop screen turn off.  It doesn't look good.  It would be better to turn off the laptop display right at LightDM, so that the VGA screen wouldn't flash to black for a second, when I login.

Here's the output of xrandr:

```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0* 
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```Thank you for the help!

---

### Post by GameX2 on 2013-02-09
Anyone can help?

I have this script, now in /etc/lightdm:

```

#!/bin/bash

XCOM0=`xrandr -q | grep 'VGA1 connected'`
XCOM1=`xrandr --output LVDS1 --primary --auto --output VGA1 --auto --right-of LVDS1`
XCOM2=`xrandr --output LVDS1 --primary --auto`
# if the external monitor is connected, then we tell XRANDR to set up an extended desktop
if [ -n "$XCOM0" ] || [ ! "$XCOM0" = "" ]; then echo $XCOM1
# if the external monitor is disconnected, then we tell XRANDR to output only to the laptop screen
else echo $XCOM2
fi

exit 0;
```

Can we just make this really simple, and display only the VGA monitor when it's connected, and (of course) only the laptop monitor when the VGA is not connected (obvious) ?
I'm hoping this would solve the problem of the resolution change flash (The screen blink to black, I want to avoid that).

Sorry, I'm not very skilled with scripts.
Thanks, I appreciate the help!

---

### Post by GameX2 on 2013-02-10
Sorry for the triple post. :S  I did progressed so far, I've did this simple script to launch at LightDM startup:

```
#!/bin/bash

xrandr --output LVDS1 --primary --auto --rate 60 --off
xrandr --output VGA1 --mode 1280x1024 --rate 60

exit 0;
```

And I have this when the Desktop start:

```

#!/bin/bash

xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1280x1024 --rate 60

exit 0;
```

I've found that the refresh rate was not the same at the Login screen and on the Desktop.  I was hoping this script would remove the black flash, but no.
There's an annoying problem with my script that I would like to fix; how can I detect if the VGA monitor is connected?  Because now, the laptop monitor turn off, even when the VGA monitor is not connected..

Thank you very much.

---

