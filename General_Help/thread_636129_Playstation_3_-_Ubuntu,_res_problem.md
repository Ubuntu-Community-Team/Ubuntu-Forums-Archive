---
title: "Playstation 3 - Ubuntu, res problem"
date: 2007-12-09
forum: General Help
---

### Post by desertboy on 2007-12-09
I've bought a HPw2207h 22inch monitor for my PS3, it has a HDMI socket on it and games work fine on it (It's native res is 1680x1050 but both 1080p and 720p games work fine so obviously the hardware scaling is working. PS3 ubuntu on the other hand isn't working well at all. I can only get 480p or 576p working, ideally I would like 1680x1050 but 720p or 1080p scaled would be alright as well.

---

### Post by matthewcraig on 2007-12-09
There is no PS3 version of Ubuntu, as far as I know.  It may very well work, but you would have to find a community to officially support that architecture.  From what I've heard, only Yellowdog Linux is supported on PS3 architecture.

PSubuntu.  Hmm...

---

### Post by Vietzomb on 2007-12-09
ps3 ubuntu is at psubuntu.com. instructions on how to install are there as well, check it out. enjoy!

---

### Post by desertboy on 2007-12-09
I've installed Gutsy on the PS3 it's res problem.

I've tried a few games now all alright but Ubuntu is just giving crazy screens like it's bypassing the scaling hardware.

---

### Post by desertboy on 2007-12-12
Bump

---

### Post by yimmmy on 2007-12-12
have u guys ever thought of checking out the psubuntu website???
its there..
[http://psubuntu.com/installation-instructions/setup/](http://psubuntu.com/installation-instructions/setup/)
heres a tut on how to fix ur problem works fine.

---

### Post by desertboy on 2007-12-14
No tried all that before I posted here, my monitor will support 720p & 1080p (scaled) as the games I own are running in those mode's fine but Ubuntu will only run in 480p or 576p.

When I run in ubuntu 720p or 1080p it's a small window right at the top of the screen, flickering really, badly and repeated 3 times next to each other, I'll try and get a shot photo today.

PS3 is connected through HDMI. (This is the only computer monitor I've seen with HDMI on it.)

What I ideally want it to be able to run in 1680x1050 but anything higher than 576p would be good.

---

### Post by desertboy on 2007-12-19
Bump still can't get higher than 576p, it makes Ubuntu unusuable and is frustrating because games work fine in 720p & 1080p

---

### Post by desertboy on 2008-01-02
Still can't figure it out is it even possible to get a PS3 to run at 1680x1050.

---

### Post by 1oki on 2008-01-02
well why dont you set the output to 480. it's not HD, but at least it will work without flickering. 

I am going to be installing Ubuntu on my PS3 tonight, and try to get it working! :)


maybe its an HDMI issue... have you tried connecting using Component or RCA?

and for those of you who say its not supported by ubuntu yet...
[http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)

---

### Post by desertboy on 2008-01-09
it works in 576 without any flickering, it's a pc monitor with 1 HDMI and 1 VGA in that's it.

Games out put fine in other res's.

Have you ever tried running Ubuntu in low res's it's almost unusuable, no web browsing, no HD movies, open office will be painful. I've kind of given up getting it to work until my budget stretches to a HDTV but it's kind of sad as it's obviously something the PS3 kernel has support for HDMI monitors but not linux kernel's. Good luck, TBH I shall be a lot more interested when they get accelerated graphics and access to other 1/2 the ram, then I see it as a viable alternative to a pc for most functions I perform and a full blown media centre.

---

### Post by desertboy on 2008-01-22
I solved the problem, it was a simple case of me not RTFM. You can't test the resolution from an x window. When I added ps3videomode to the startup the res change worked.

Can't get 1680x1050 but I can get 1280x768 which will do, 1080p looks far too small scaled on a 22" 1680x1050 monitor.

It's too slow to be useful really and unless we get accelerated graphics drivers access to a bit more ram and better repository support I can see it being a bit of a dead duck.

---

### Post by gt_momo on 2008-03-23
I've got basically the same kind of monitor as desertboy. A 22 inch Sceptre (the price was right) LCD with HDMI, DVI and VGA.

What I really want to know is if it's possible to get Ubuntu to kick out it's native resolution of 1680x1050 over HDMI or if there are problems with the HDMI format.

I was thinking that maaaaaybe an HDMI to DVI converter would work.

What do you think?

---

### Post by gt_momo on 2008-03-25
Any...body...?

---

