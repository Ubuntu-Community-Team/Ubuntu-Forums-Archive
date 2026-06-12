---
title: "Mouse sluggish"
date: 2012-11-24
forum: General Help
---

### Post by heracles on 2012-11-24
Since a new installation of the latest Ubuntu with all updates I now experience a strange mouse problem. Seemingly randomly the mouse movements will slow right down, its just like a slow motion mouse I have to wait whilst the pointer trvels very slowly across the screen. I though it was another programme running that caused the problem so I have stopped all redundant programmes in the start up. The problem however is still there and the slow mouse movement just comes and goes without any reason. I can only imagine it is another programme suddenly running in the background but I cannot seem to find out. Any ideas please?

---

### Post by 2F4U on 2012-11-24
Open Task Manager and let it run. When the mouse slows down again, check in Task Manager if CPU load is high, and if so, also check what program causes it.

---

### Post by heracles on 2012-11-25
Thank you I will experiment with your suggestion.

---

### Post by mvglasow on 2012-12-07
Same issue here... it's a HP EliteBook 6930p running Ubuntu 12.04, fresh install with latest updates (a refurbished laptop that I just picked up), using Gnome Classic (no effects).

The issue will come and go seemingly at random. For a while the mouse will respond normally; then for no apparent reason I move the mouse and only after a certain delay the pointer will move very slowly into the direction I pushed the mouse, and when I stop moving the mouse, the pointer will still keep creeping further into the same direction for about another second.

Both mouse and touchpad are affected by this. Other graphics operations appear normal.

I looked at CPU load in a few instances, but the CPU was mostly idle with both cores somewhere between 15 and 20% load. So the processor is not the bottleneck here.

I had the most extreme occurrence of it after I placed the laptop in a docking station (for the first time) with an external monitor attached. I got delays of up to a second, to the point that the mouse became completely unusable.

In two instances the mouse went back to normal responsiveness after I closed an open application - Brasero in one case (though no burn or other was in progress when the problem started), display settings in the other case (after I hooked up the external monitor).

Up to now, I have used Ubuntu 12.04 on a Fujitsu-Siemens Lifebook S7010 for a few months and never had such issues. I have also never experienced this when using a 12.04 live USB with a HP Compaq 6910p (with an Intel 965 graphics adapter - some models with the same name ship with an ATI Radeon, similar or even the same that the 6930p uses).

So I suspect it is an I/O issue, not a processor issue, related to hardware, possibly graphics hardware (since it was worst just after I hooked up the new display), and possibly (though I'm not sure about this) related to some application actions that trigger it.

Edit: just filed a bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1087677](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1087677)

---

### Post by zerubbabel on 2012-12-16
I have had a similar experience after upgrading to 12.10 (Kubuntu). It seems to occur somewhat consistently after I leave the computer idle for awhile, then I go back and continue what I was doing, but the point is slow to respond, and then overruns where I'm trying to position it, and typing is also sluggish. But then after a minute or two, everything is back up to speed, with no delays. This is on a fast Intel Core i5 with 16GB RAM, and only LibreOffice, Thunderbird, and Jitsi running.

---

