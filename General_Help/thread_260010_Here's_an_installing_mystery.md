---
title: "Here's an installing mystery"
date: 2006-09-18
forum: General Help
---

### Post by Fred Doolie on 2006-09-18
The Alternate Install CD of Dapper does a MUCH better job than the live/install CD.

1) The L/I CD won't allow 1280x1024 as a screen res option.
2) The L/I CD won't find the repositories during install.
3) The L/I CD assumes IPV6 so I have to do that editing of /etc/modprobe.d/aliases and reset the repositories and other stuff.
4) After install with the L/I CD I need 127 updates. The A CD only needs 22.


The Alternate CD automagically sets all that stuff up fine. I guess it really bangs the hardware and the L/I CD just makes assumptions. Oh, yeah, the A CD did ask me what screen resolutions I wanted so that part makes sense but what about the rest? 

Does the A CD try all kinds of network settings during install and set up for what works best?

You guys with wireless networking, does either CD see that and set it up or must that be done by hand?

---

### Post by kerry_s on 2006-09-18
I always use the alternate cd, i used the live cd 1 time and did not like it. The alternate installer has never let me down yet and i've used the server install alot just playing around with different WM's and get exactly what i want on my system with no bloat.

---

### Post by orb9220 on 2006-09-18
I have used the liveCD only on 3 different installs.

1) Screen res was always 1024x768 for my nvidia cards. And yes to get 1280 you have to install the nvidia drivers.

2) Not unless your connection is found and setup on liveCD. Mine was for D-Link dwl-510b1 wireless card. So if networking is not found during liveCD then of course the repo's won't be found.

3) Again what I find to be needing alot more work on is wireless and networking to work from the liveCD. Tho it does do pretty good for most there is still a chunk of people that can't get it to work.

4) Nope 6.06.1 is the latest which takes care of about 130 or so of those updates in the iso [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

It may be you got the 6.06.1 alternate but only the 6.06 desktop which would explain the difference between the two.

---

