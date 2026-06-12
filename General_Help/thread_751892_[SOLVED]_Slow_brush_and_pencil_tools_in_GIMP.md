---
title: "[SOLVED] Slow brush and pencil tools in GIMP"
date: 2008-04-11
forum: General Help
---

### Post by Eastisle on 2008-04-11
Hi,
Well I've been trying to transition to  the GIMP after trashing XP with Photoshop. One thing I've noticed is that the brush and pencil tools lag when being used. That is, the tools trail behind my cursor by as much as a second when painting.  Is anyone else having the same problem? I've adjusted the cache by not much improvement. 

By the way I have 2 gigs of RAM and dual core pentium D. TIA.

---

### Post by FuturePilot on 2008-04-11
What kind of graphics card do you have? And have you checked for drivers in System&#8594;Administration&#8594;Restricted Driver Manager? Everything is smooth here.

---

### Post by Eastisle on 2008-04-11
I'm running the ATI restricted driver. Card is Radeon X300. I overlooked the video card as a possible cause. I guess its video card related then?

---

### Post by FuturePilot on 2008-04-11
It could be. Are you running Compiz?

---

### Post by Eastisle on 2008-04-11
No I have it disabled for now. Though, I'm capable of running it after I did some changes here and there. Thanks by the way. :)

---

### Post by kesman on 2008-04-11
Does this occur with any size of images and any size of the brush? Does it make a difference if you paint over a simple JPG-img rather than a complex TIFF or similar? Also, what version of ubuntu and Gimp are you running?

EDIT: also found this: [https://launchpad.net/ubuntu/+source/gimp/+bug/41798](https://launchpad.net/ubuntu/+source/gimp/+bug/41798)

---

### Post by Eastisle on 2008-04-11
I've varied image sizes, brush sizes, and file types. The problem is the same for all of them. One thing to note is that if I use any of the painting tools slowly the lag is nonexistent. It only happens with medium to quick strokes.  As far as GIMP I'm running 2.4.2 and Gutsy. Thanks to you also.

---

### Post by DirtDawg on 2008-04-11
Apologies ahead of time if this suggestions are obvious. 

In Gimp, in file>preferences you can change the [tile cache size]("http://www.gimp.org/unix/howtos/tile_cache.html") and the "number of processors to use." Maybe adjusting one or both of these will help?

---

### Post by Eastisle on 2008-04-11
Thanks DirtDawg. I checked over the cache settings just in case, but no improvements. Now that I think of it I think the lag has been there since back when I had Feisty. At the time I was using Photoshop so I paid no mind to it. Anyone else think it might be related to my video card? I also use Inkscape but all is smooth and running well.


EDIT: I decided to disable my ATI restricted driver just to see if it changed anything. It did. GIMP works smoothly, so I came to the conclusion that its a video card related problem. I'm going to replace it soon after doing some research. Thanks for your time and suggestions guys.

---

