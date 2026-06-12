---
title: "Touchpad Sensitivity"
date: 2006-11-18
forum: General Help
---

### Post by thecynicality on 2006-11-18
My touchpad is extremely sensitive to touches, and im wondering if i can adjust the sensitivity or disable the click by touch.

---

### Post by strabes on 2006-11-18
change the sensitivity of touch? check out my blog post [here](http://strabes.wordpress.com/2006/11/04/turn-off-annoying-touchpad-tap-click-in-ubuntu/)

for the sensitivity of movement, i have another post [here](http://strabes.wordpress.com/2006/11/04/change-your-touchpad-sensitivity-in-ubuntu/)

---

### Post by thecynicality on 2006-11-18
When i open the file to edit i did a search for touchpad, and synaptics and it can't find either.

---

### Post by thecynicality on 2006-11-19
Still need help.

---

### Post by thecynicality on 2006-11-20
Anybody?

---

### Post by rvickers on 2006-11-21
I'm fighting the same problem, I have a SynPS/2 Synapticts TouchPad which is listed in /proc/bus/input/devices and so far I haven't found a solution...:(

---

### Post by jrohde on 2006-11-25
I have the same problem - no mention af a touchpad in xorg.conf. I'm using a Acer Ferrari 4000, and the touchpad works, but it's too sensitive.

---

### Post by spesheled1 on 2006-11-26
The info in that article about adjusting the touch sensitivity did the trick for me, thanks strabes.8)

---

### Post by CFC on 2006-12-08
Thank you for the tip.
I was able to adjust the sensitivity of the tap. Now it doesn't go bonkers when any time I simply graze it.

Thanks,
CFC

---

### Post by Bill_MI on 2007-03-12
> **strabes said:**
> change the sensitivity of touch? check out my blog post [here](http://strabes.wordpress.com/2006/11/04/turn-off-annoying-touchpad-tap-click-in-ubuntu/)

Thanks, strabes.  I confirm this is the best I've had the Dell Latitude C810 touchpad working.  A value around 80 is quite usable.

I'm exploring basic touch sensitivity tweaks, too.  Meaning pressure, not time.  If I find anything I'll post it.  BTW, this C810 driver always uses "Alps" in Windows but it obviously is controlled in this Synaptics section.

EDIT: I found a highly commented xorg.conf description [HERE]("http://www.cs.utexas.edu/~erkin/home/tools/xorg.conf").  You can play with your touchpad all week. :D

---

### Post by Fenrirwulf on 2008-01-09
Thanks again Strabes!
  Worked on my Dell D600. Yipeee!:):)

---

### Post by aktoads on 2008-01-10
It sounds like everyone is having an opposite problem as myself.  My touchpad is hardly moving at all.  Now the USB mouse works fine?  I did put a post on the forum about touchpad slow response.  Any ideas?  It takes me 8 swipes of the touchpad to cross the screen.  It worked well for a bit, now??? (I don't know what I did out of the ordinary, and am still learning how to get around in Ubuntu/Linux.)  

Thank you

---

### Post by raquo on 2008-01-12
> **Bill_MI said:**
> EDIT: I found a highly commented xorg.conf description [HERE]("http://www.cs.utexas.edu/~erkin/home/tools/xorg.conf").  You can play with your touchpad all week. :D

Yeah, that one rocks! Thank you :popcorn:

---

