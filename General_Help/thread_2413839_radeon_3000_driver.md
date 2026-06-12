---
title: "radeon 3000 driver"
date: 2019-03-02
forum: General Help
---

### Post by jgw on 2019-03-02
I just finished doing stuff to my machine.  One of those things was to remove the display card and use the display connection from the motherboard.  That display is a radeon 3000.  I did a sudo lshw -c video | grep configuration and see that display=radeon.  I am assuming that means that my driver is "radeon".  I removed the card for no reason than it was something that I could probably do without.  Now I am wondering if I was right.

When I was using the card I had a resolution of 1920x1080 and now I have a resolution of 1024x768.  This being the case I was wondering if there are better drivers available.  My motherboard is about 7/8 years old.  Settings tell me my graphics are AMD® Rs780

this is a different computer than my signature says:
Computer
Processor	                 AMD FX(tm)-6300 Six-Core Processor
Memory	                 7892MB (3052MB used)
Machine Type	         Desktop
Operating System	Ubuntu 18.04.2 LTS
Display Resolution	1024x768 pixels
OpenGL Renderer	AMD RS780 (DRM 2.50.0 / 4.15.0-45-generic, LLVM 7.0.0)
X11 Vendor	The X.Org Foundation
Audio Devices
Audio Adapter	HDA-Intel - HDA ATI SB
Audio Adapter	USB-Audio - USB Device 0x46d
Audio Adapter	HDA-Intel - HDA ATI HDMI

Thank you.................

---

### Post by jgw on 2019-03-05
Since there have been no replies I thought I would try to do this myself.  I may have created a problem for myself but I never did get the resolutions to change.  Here is what I did (any thoughts are appreciated):

greg@gregdown:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DVI-0 disconnected (normal left inverted right x axis y axis)

greg@gregdown:~$ sudo xrandr --newmode 1920x1080 148.5 1920 2008 2052 2200 1080 1089 1095 1125 +hsync +vsync

greg@gregdown:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DVI-0 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x58f) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1089 end 1095 total 1125           clock  60.00Hz

greg@gregdown:~$ sudo xrandr --newmode 1920x1080 148.5 1920 2008 2052 2200 1080 1089 1095 1125 +hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25
greg@gregdown:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DVI-0 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x58f) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1089 end 1095 total 1125           clock  60.00Hz

---

### Post by CatKiller on 2019-03-05
> **jgw said:**
>  This being the case I was wondering if there are better drivers available.  My motherboard is about 7/8 years old.  Settings tell me my graphics are AMD® Rs780

I believe radeon is the correct driver for that card.

I think you're on the right track with the xrandr command. Having created the new mode, I believe you then need to use addmode to make it available for a particular output.

I haven't used AMD graphics hardware, nor played around with xrandr, though.

Another way to do it is to specify the HorizSync and VertRefresh ranges for your monitor in your xorg.conf.

---

### Post by jgw on 2019-03-06
Thanks for the reply.  I will continue to figure it out (hopefully)

---

