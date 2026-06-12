---
title: "Driver for HP M70 monitor??"
date: 2007-03-11
forum: General Help
---

### Post by YoungCthulhu on 2007-03-11
Gidday, :) 

Can anyone direct me to a source from where I can download a driver for my old HP M70 monitor?  I recently upgraded to a better machine (Intel Core2 duo box only) and have found that when I connect my old monitor to it I cannot get more than 800 x 600 resolution.  Previously I could get up around 1024 x 800 with Ubuntu using my old box, a P3 with only 16mB of video ram.

This one has got an ASUS V558 driver (128mB with up to 512mB using shared main RAM if available).  

Sorry if there is another posting on the forum that deals with this; I did several searches but could find nothing, but then I am a beginner. :confused: 

Cheers

---

### Post by scxtt on 2007-03-11
what manu. of videocard (or chipset) do you have? (ATI or Nvidia?) ... chances are the default 'vesa' driver can get you 1024x768 (4:3) resolution - you'll just need to add the "HorizSync" and "VertRefresh" rates to your /etc/X11/xorg.conf ...

that might sound confusing @ first, so we'll start out w/ finding those values out - if that's possible ... i'd ask google ;)

edit, found it: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=bph03695](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=bph03695)

so look for the "Monitor" section in /etc/X11/xorg.conf and make it look like:
```
[font=courier]Section "Monitor"
       Identifier   "Monitor 0"
#      Option       "DPMS" "on"
       [B]HorizSync    30-70
       VertRefresh  50-120[/B]
EndSection[/font]
```

and a "Screen" section like:
```
[font=courier]Section "Screen"
       Identifier "Screen 0"
       Device     "Adapter 0"
       Monitor    "Monitor 0"
       DefaultDepth     24
       SubSection "Display"
#               Virtual   1600 1200
#               Viewport   0 0
               Depth     24
               **Modes     "1024x768"**
       EndSubSection
EndSection[/font]
```the "Identifiers" are important, so yours might need to be different than what i've posted - don't change them if unnecessary ...

hashimoto's method will "automate" what i'm talking about above, but doesn't 'teach' you anything ;)

---

### Post by hashimoto on 2007-03-11
I had the same monitor and the problem is not in any driver.That monitor just doesn't report correct refresh rates to the system so X doesn't recognize its full capabilities.

To correct the situation, find out the technical data of the monitor (supported resolutions & refresh rates) then open terminal and run

```
sudo dpkg-reconfigure xserver-xorg
``` 

and answer the questions. When the screen allows you to select option advanced, do that and you can fill in the correct refresh rates & select supported resolutions.  After that finish off by resterting X (ctrl-alt-backspace).

---

### Post by YoungCthulhu on 2007-03-11
\\:D/  Thanks scxtt and hashimoto for your great replies!  

I will try it both ways, and look up all the commands in the O'Reilly Linux Pocket guide that I have just bought too.

Cheers!

---

### Post by jacque on 2007-11-18
Hi YoungCthulhu

> This one has got an ASUS V558 driver (128mB with up to 512mB using shared main RAM if available).  

could you (or anyone else) please tell me where can I find UBUNTU drivers for ASUS V558?

I have bought brand new monitor but cannot use higher resolutions probably because of not proper configuration of graphic card.

thank you in advance

Cheers
jacque

---

