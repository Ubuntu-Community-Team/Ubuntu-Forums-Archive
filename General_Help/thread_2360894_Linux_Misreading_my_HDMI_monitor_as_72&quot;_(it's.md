---
title: "Linux Misreading my HDMI monitor as 72&quot; (it's 40&quot;) causing desktop problems."
date: 2017-05-09
forum: General Help
---

### Post by whereismymindat2 on 2017-05-09
Hello, 
Thanks for reading. 
I recently upgraded to Optiplex and a Toshiba Flat Panel as Monitor. The Monitor is not working as it should. 
++++++++++++++++++++++++++++++++++++
The Icons are "Bleeding over" on Left side of page without the "snap to grid" use to. 
++++++++++++++++++++++++++++
Question. How can I downsize my (Workspace?) borders to over ride Linux?

Linux "thinks" I have a 72" vs. 40" HDMI monitor hooked up. (Yeah, wish I had 72" to use ad Monitor!). :-)

What's occurring is Neither the TOP: (where the Panel is to always shown) nor either side panel (even with ONE work space) is honoring the Grid Pattern I set up. 

(I even went so ridiculous as 300---after first starting at 50 not working). 
+++++++++++++++++++++++++++++++++++++++

Does a File Exist I can change? 
Is it better to change some setting/file/command line to "force" Linux to see it as a 40"?. 

Just Down sizing the "DISPLAY" settings 
CURRENT: 1920x1800 (at 60hz)----need to change this to 120hz as well. Resolution is horrible. 
Change to 1280x1024---it downsizes entire screen (large black bars down both sides)----in Pic it shows up as Grey. 
+++++++++++++++++++++++++++++++++++++++
```
In conclusion (in there a File I can manually edit) or command line or setting to change, To stop the Bleed Over and Use "FULL" capacity of Screen? 

Attached are screen shots of the "bleed" over I speak of. 

If it matters, I'm using the HDMI Port (Of Flat Panel) to connect into the DVI port of Optiplex. Some reason, the HDMI Port won't "connect" into Optiplex. *shrug*?
```




Thank you in advance!

---

### Post by efflandt on 2017-05-09
The EDID of the monitor connected with DVI or HDMI does not always indicate the correct screen dimensions, but should provide info to your computer graphics of available screen resolutions. For example it thinks that my LG 32" 1080p HDTV is a 52" Goldstar. But 1080p is 1920x1080 pixels, so actual size of the screen should not matter and you would think that digital graphics should just work. However, apparently horizontal and vertical timings can vary somewhat. My LG HDTV has a setting called "Just Scan" that tries to size and center whatever video signal it is receiving better than its "16:9" setting. I think Samsung calls that "Fill Screen". I don't know if your monitor has any adjustments for sizing or centering (or overscan/underscan).

NVIDIA X Server Settings has an "Underscan" slider in its settings to reduce overscan. Not sure if the AMD driver tool does. If you have integrated Intel graphics and no adjustment on the monitor itself, you might need to play around with xrandr settings. I don't know what that dialog is you show that appears to have adjustable margins. Back 20 years or more ago there was a gui that would be used to initially configure X to fit your monitor. But that seems to be missing from modern Linux versions that think X should be able to automatically figure everything out by itself.

PS: I am using DVI to HDMI cable because I think the HDMI port(s) on my graphics card might be mini-HDMI and I was using my HDMI cables for other things.

---

