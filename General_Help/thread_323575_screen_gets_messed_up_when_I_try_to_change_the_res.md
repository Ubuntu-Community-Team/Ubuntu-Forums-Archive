---
title: "screen gets messed up when I try to change the resolution"
date: 2006-12-22
forum: General Help
---

### Post by ACGarib on 2006-12-22
Whenever I try to change the resolution, the screen gets completely messed up. The top quarter of the screen turns red or blue and everything but the mouse cursor gets shifted down a few inches. Also, the mouse cursor doesn't work correctly anymore (I have to put the cursor about 3 inches above what I want to click in order to click it). A few seconds later, the screen turns completely blue or red. When it is completely blue or red, if I mouse over a button or scroll up and down a web page, the button or web page will show up again. Eventually the screen resolution automatically goes back to 1280 x 1024 because I didn't click the "keep this resolution button". Although the resolution went back to what it was, the top part of the screen that is to the left and right of the top menu bar stays red or blue and the wallpaper is shifted down so the top of the wallpaper is touching the bottom of the menu bar. restarting X will fix these problems.

I am running beryl + aiglx and edgy with a radeon 9800 pro and the radeon drivers.

My question is, how do I change the resolution without the screen getting messed up?

---

### Post by Howler9443 on 2006-12-22
I would check the scan rates and make sure they match your monitor. A lot of times if you don't match your scan rates it will do things as you described.

Check your /etc/X11/xorg.conf for the scanrates xorg is trying to use and compare them with what your monitor is capable of. Adjust xorg.conf accordingly.

Thats where I would start.

I hope this helps.

---

### Post by ACGarib on 2006-12-22
I think I've got the horizsync and vertrefresh right. Here's the monitor section of my xorg.conf. 

Section "Monitor"
	Identifier	"DELL E773c"
	Option		"DPMS"
	HorizSync	30.0-70.0
	VertRefresh	50.0-160.0
EndSection

[B]I think I've narrowed it down to beryl because I can successfully change the resolution with metacity, but not beryl and compiz. 
[/B]
Any ideas?

Also, after I reconfigured my xorg.conf, I can no longer go from metacity to beryl without X restarting.  I don't know what to do to get this working again.

---

