---
title: "How to adjust screen resolution?"
date: 2013-02-27
forum: General Help
---

### Post by healee on 2013-02-27
I try to follow [http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/) to do a virus scan.  When I get to the last bit where I want to start the scan, the "Start" scan button is out of reach.  It is well below the bottom of the screen.  I can't move the dialog upwards or re-size it so that I can get to the button to click it.

Nevertheless I can't find anywhere I can re-define the screen resolution so that I can get to the button.  It is a surprise to me that the screen resolution cannot be adjusted.

Please tell me what I have missed!

I run the ubuntu 9.04 Desktop Edition as a live CD without installation.

---

### Post by matt_symes on 2013-02-27
Hi

Why on earth 9.04 ? :D

Open a terminal and type```


xrandr
```This will give you a list of supported resolutions.

Here is mine:

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
```You then select the resolution with

```
xrandr -s <resolution>
```so for me to select 800x600 i would type

```
xrandr -s "800x600"
```Kind regards

---

### Post by TheFu on 2013-02-27
> **healee said:**
> I run the ubuntu 9.04 Desktop Edition as a live CD without installation.

I'd like to help, but 9.04 is really, really old and shouldn't have been used since 10.10 was released.

However, **xrandr** might be useful, assuming that you don't want to manually edit the /etc/X11/xorg.conf file.

---

### Post by healee on 2013-02-28
Thanks matt_symes
I am testing the command on another laptop.
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1366 x 1366
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1366x768       60.1*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
They I try the following but it comes up with an error message as follows though xrandr has said maxium 1366 x 1366.

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] xrandr -s 1366x1366
Size 1366x1366 not found in available modes

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] xrandr -s "1366x1366"
Size 1366x1366 not found in available modes
&#12288;

---

### Post by healee on 2013-02-28
Thanks TheFu.

Though I have had ubuntu 10.04.1. I followed the instruction of the web page [http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/) in order to minimize complication.

Sometimes I wonder why the next version of ubuntu has to be so different.  Aren't they supposed to be backward compatible, especially in terms of the usage of commands?

---

