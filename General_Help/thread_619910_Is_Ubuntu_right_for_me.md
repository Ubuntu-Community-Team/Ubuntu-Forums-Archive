---
title: "Is Ubuntu right for me?"
date: 2007-11-21
forum: General Help
---

### Post by krakerjak on 2007-11-21
I am waffling at the moment, I have Feisty installed on an old desktop computer of mine.  

It is used primarily as a music server (MPD w/Pitchfork, and Icecast) & for network storage (Samba).  The problem I have is that something with this box locks up my router occasionally.  I am sure it is due to this computer because I have had it off for 2 weeks, with no router problems at all.  I don't know if I have screwed up the install of something or not.  

So my question is this.  Do I need to re-format/re-install, or try another distro, or try the server install?  I use it headless with either VNC or Webmin depending on what I need to do.

Anyone have a suggestion?

KJ

---

### Post by elctb on 2007-11-22
First of all, the problem is with the router. There should be no reason whatsoever that any machine connected to the network can crash a router. Now, having said that it's possible that Feisty exposes a bug on the router that eventually leads to a crash.

I would first check if it's possible to upgrade the router software. If that's not possible and you're 100% sure Feisty is crashing the router, upgrading to a newer Ubuntu release might make the problem disappear, just might..

---

### Post by Nunu on 2007-11-22
Your computer crashing the router does not sound like a possibility to me. are you sure that someone or some thing isn't doing a brute force or denial of service attack from the outside. Check the router logs first before reinstalling or upgrading.

I know it sounds dodgy but have a look at that first. and see of you can see high volumes of traffic from both sides of the router.

---

### Post by krakerjak on 2007-11-22
Thanks for the replies

> elctb wrote:  First of all, the problem is with the router.

Normally I would agree, however I've had the router for about 3 years, without issue.    

> elctb wrote:  I would first check if it's possible to upgrade the router software.

I am already running the most recent firmware.

> Nunu wrote:  Check the router logs first before reinstalling or upgrading.

Logs really have anything in them.

I am looking at changing the router firmware to [tomato]("http://www.polarcloud.com/tomato"), I just hate to do anything to the router.  The problem only appears when my Ubuntu box is connected.

---

### Post by st33lwolf on 2007-11-22
i dont know if this is true but i had the same problem with my router...

i had a linksys wrt54g that was about 3 years old and just crapped out on me... it would run for about 4 hours straight and once u started putting traffic through it. ex playing a game online. it would just freeze up and u would have to restart it...

possibly your router is just dieing and u need a new one...

firmware upgrade might help, i never tried that though cause i wanted a new router anyway...

---

### Post by krakerjak on 2007-11-22
Turns out the problem is with the router.  I had it go down today, without the Ubuntu box connected.

I flashed the tomato firmware today, I'll see what that does for me.

Thanks for the help.
KJ

---

