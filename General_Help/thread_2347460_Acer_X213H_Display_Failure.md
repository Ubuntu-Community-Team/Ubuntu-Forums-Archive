---
title: "Acer X213H Display Failure"
date: 2016-12-25
forum: General Help
---

### Post by rwe061 on 2016-12-25
Ubuntu 16.04 Dual Boot with Windows 7
Intel I7 Skylake on chip graphics
Display: Acer X213H

I built a new computer and trying to use my old display monitors which no longer work for Ubuntu.

I hope someone can help me in the right direction to investigate this.

1. my BIOS displays properly on the Acer monitor
2. my grub boot selector displays properly
3. If I boot Windows 7, it displays properly
4. if I boot ubuntu 16.04, the X213H just goes dark after grub.


Thanks

---

### Post by rwe061 on 2016-12-28
I still can't get my displays running on Ubuntu after a motherboard upgrade.

Does anyone have any advice on how troubleshoot a display monitor problem ?

It is not detecting the monitor properly.  

If I plug in the Acer monitor then I can not see the display, it is either blank.  

Works when I boot windows on the same machine.

I have a TV with HDMI port that seems to work fine, so I know that Ubuntu display is working.

---

### Post by rwe061 on 2016-12-29
For others that may need help on this sort of problem the following post may be helpful.  Search down to the description of the program powerstrip which accesses a lot of information on the display monitor and display controller.  PowerStrip runs under windows.  It reports my display model number differently than the model marked on the display.

[https://www.x.org/wiki/FAQVideoModes/#head-82230a582646cbf28ac41dec2139732ee868e0d2](https://www.x.org/wiki/FAQVideoModes/#head-82230a582646cbf28ac41dec2139732ee868e0d2)

Apparently Linux is unable to get the information from the monitor, which is actually available.  Following the details in the xorg wiki post I was able to get this:

   > [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]PowerStrip timing parameters:[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]1920x1080=1920,88,44,148,1080,4,5,36,146891,518[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] 
 [/LEFT] [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]Generic timing details for 1920x1080:[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]HFP=88 HSW=44 HBP=148 kHz=67 VFP=4 VSW=5 VBP=36 Hz=59[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] 
 [/LEFT] [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]VESA detailed timing:[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]PClk=146.89 H.Active=1920 H.Blank=280 H.Offset=72 HSW=44 V.Active=1080 V.Blank=45 V.Offset=4 VSW=5[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] 
 [/LEFT] [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]Linux modeline parameters:[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]"1920x1080" 146.891 1920 2008 2052 2200 1080 1084 1089 1125 -hsync -vsync[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] 

Later I'll try out this information using xrandr and see if it works.  

 [/LEFT]

---

