---
title: "getting up and running"
date: 2014-06-04
forum: General Help
---

### Post by jgw on 2014-06-04
I have spent the last couple of days moving my tv computer from windows to ubuntu (sabnzbd, sickbeard, couchpotato, xbmc, etc).  I did this on a workbench with a monitor.  Once I figured I had it all done I hooked it up to my TV.  Ooooops!  I now have 2 problems.  I have an nvidia gt 440 display card on this machine.  I installed the nvidia driver for older cards.  Everything was dandy on the monitor.  On my tv, however, the launch bar went away, the top bar also disappeared.  The native display size of my screen is 1920 by something.  I went all the way down to 1020x768 and the launchbar is almost there but the top is still gone.  I then tried to install the nvidia x settings program.  I said install, put in my password, and then put a cursor over it on the launchbar and found it was waiting to install (its now been waiting to install for 3 hours <g>).  I checked that out and it seems its a bug.   When I was putting this all together I was plugged into a lan (wired).  given my problems with the screen there is little I can do about that one either (no top bar, no unity).  Tomorrow I will take the machine back to my bench and try to fix the problems.  I have no idea if I am going to be able to install the nvidia x setting program or not and, as far as I know, that's what I am going to need to make this work.  I do know that nvidia has a unix driver on their site for my display card.  

I should mention that I had this machine running, with ubuntu, before, under 12.04, with few real problems.  At that time I had some other kinds of problems and finally moved to windows but felt it was time to make another run at it. 

So, if anybody has any suggestions for me I would appreciate them (be kind)

---

### Post by TheFu on 2014-06-05
Do NOT install drivers from anywhere outside the normal Ubuntu repos.  Definitely avoid direct downloads from nvidia.  Newer is NOT always better.
For a streaming server, avoid wifi. Use wired ethernet. If that isn't possible, get a 500Mbps power-line networking adapter. Wifi sucks when solid, constant streaming is needed.

**xrandr** should let you pick the display resolution supported by your TV.  Try to go with the native resolution - whatever that is.  Just because a TV accepts 1080p inputs, that doesn't mean it is useful to send it those when it is a 768p native device. You'll need to look in the TV manual to find the native resolution (or google it).

---

### Post by jgw on 2014-06-05
Thanks for the reply.  I do not stream but download so I have no problem with the wifi thing (but the power-line networking thing is interesting.  I have wondered, for years, if those things actually worked <G>)  

The problem with the resolution is that there is resolution and there is screen size and they are different things.  I have been messing with these things for a very long time and I still get confused about the difference between the two and what does what.  I will give xrandr a drive to see how that works.  The best way, I think, is to get something that will allow me to deal with the edges of the screen which I can do under windows and used to do with ubuntu but that was a couple of years ago.

Thank you, very much for your thoughts on this one, its appreciated.

---

### Post by TheFu on 2014-06-05
Powerline networking does work, with some caveats.  Early versions sucked and had very little security. Currently available ones have much stronger device-to-device encryption and have stable speeds if there aren't any shorts/breakers in the middle.  Don't expect the advertised speeds, but 50% of 500Mbps is still 250Mbps - faster than many home network cards. Plus that is stable speeds like wired ethernet, not like wifi where speeds are best case, if there isn't any interference and if atmospheric conditions and distance is perfect (which never happens).  Wifi throughput fluxuates ms by ms and can vary wildly ... to the point that I find it only useful for light email and web surfing here.  For a few years, I did over 1,000 wifi deployments as my day job. It sucks and almost any other wired networking technique is better long-term.  Still, if there isn't any choice, there are ways to setup a better than average wifi network by getting better APs than a sub-$100 home router will support. OTOH, for many people, a $20 home-wifi router appears to work jsut fine for their simple needs - they've never had multiple HiDef MPEG2 streams going to different clients concurrently, I guess.

You want to find the "native resolution" of the TV.  Screen size doesn't matter at all. I think the other thing you are complaining about is overscan - TVs have that. Some let you control it in their setup screens, others through the "service screens" and some don't allow overscan control at all.

If the drivers support it, then you can control it under Linux.  It is up to the GPU vendor to provide good drivers.

---

### Post by jgw on 2014-06-05
Thanks for the reply.

the native resolution of my screen is 1920x1080 and my screen size is 60" diagonal.  I am not sure what you mean by overscan but if you mean does stuff run off the screen - it does.  I also found that continued no matter what I set the resolution to.  I now have the nvidia setting thing installed but it doesn't seem to work, other than allowing me to fill in some check marks to set it up.  The tv is a reasonably new samsung (not particularly smart).

Thoughts?

---

### Post by TheFu on 2014-06-05
That is **overscan** you are seeing.  Lots of google answers for that.

---

