---
title: "Odd computer behaviour"
date: 2019-11-16
forum: General Help
---

### Post by kristjan.liiva1 on 2019-11-16
I was running Ubuntu 18.04 and at some point my computer started to restart. I think it started when I used the computer for around 7 hours or so and then it happened again after 2 hours or so. So the first restart took considerable longer than the subsequent ones. The behaviour seemed to reset once I turned of the computer for a while. Over time the times started to get short and short. Eventually I think I could use the computer for about half an hour and then then it started to restart before I managed to even log in (it also started to restart without me using full screen applications too at an earlier point in time).

I have taken my computer to diagnostics and they said that everything seems to be fine with the hardware (they had it under heavy load for 21 hours and it was working fine). They suggested it is an software issue.

I've reinstalled Ubuntu multiple times and I also installed Lubuntu once. The problem is still there and seems to be unaffected from reinstalling the OS.

The computer also seemed to work fine when I used LIVE session of the bootable USB stick.

Any ideas what is going on here?

---

### Post by Autodave on 2019-11-16
Some info on your system would be helpful.

When I see a problem like yours, the first thing that I check is memory.  A bad RAM stick will do exactly what yours is doing.  However, it puzzles me that someone ran it for 21 hours without a hiccup.  So, my next thought be overheating.  If your machine is a laptop, try it w/o sitting it on something soft: use a hard table, counter, etc.  Do not hold it on your fuzzy pants! :-)

If this is a desktop, where is it located?  Is it getting access to cool air?  (You don't have it sitting next to a heating source?)  Is it in a cabinet like I see on a lot of PC desks?  That is not good: it needs to be open, not enclosed.

How many USB devices do you have hooked up to it?  They could be drawing too much of the 5V power and overheating the power supply.

---

### Post by dragonfly41 on 2019-11-16
Adding to the list of ideas above ... if you have a laptop ...

try laptop with internal battery removed and only mains supply through PSU
try laptop with only internal battery and no mains supply through PSU

---

### Post by kristjan.liiva1 on 2019-11-16
My system is a desktop. It's located on a desk, pretty far from heating source and is surrounded by empty space of at least 7 cm on all sides. I think it can be a bit dusty though (I haven't cleaned it in a while), so maybe that is why it could be overheating.

Regarding RAM, I did three memtests. Two using the bootable USB and one without it (from something similar to GRUB menu). There was a restart during the middle of the test when it wasn't from the bootable USB. I'm not sure what happened during the first test from bootable menu (I wasn't in the room, but I suspect that there was a restart because I think there wasn't enough time to complete it). I was observing the computer during the second one and it managed to get to 100% on the first one with zero errors (I stopped it after that).

I guess my next bet is to clean the computer, remove half of the RAM and see what happens.

EDIT: forgot to add that I have 3 USB devices connected (bootable stick, keyboard and mouse)

---

### Post by dragonfly41 on 2019-11-16
> [COLOR=#000000]I have taken my computer to diagnostics and they said that everything seems to be fine with the hardware (they had it under heavy load for 21 hours and it was working fine). They suggested it is an software issue.[/COLOR]

Since it has proven to have worked in an external environment (workshop) there is a rare possibility that your own mains supply is not clean.
I don't know how you might check this possibility other than again taking desktop to another site for tesing. Do you have any local devices which might cause spikes on mains supply? This is a long, long shot.

...

But again you write this ... which goes against above theory ...

> [COLOR=#000000]The computer also seemed to work fine when I used LIVE session of the bootable USB stick.[/COLOR]


...

[Further thought] Did you take your monitor to the workshop or only the desktop (with any items missing)?

---

### Post by dragonfly41 on 2019-11-16
Added note.

There are some ideas in related threads if you search around ..

[https://askubuntu.com/questions/880875/ubuntu-restarts-randomly-and-there-is-no-log-about-the-reason](https://askubuntu.com/questions/880875/ubuntu-restarts-randomly-and-there-is-no-log-about-the-reason)

---

### Post by HermanAB on 2019-11-17
Note that in many parts of the USA and Canada the mains voltage is low and noisy.  Laptop computers have a built in battery and PSU, so they are generally more reliable than a desktop.  If your PC worked fine in a repair shop, but not where you live, try to add a UPS.

---

### Post by kristjan.liiva1 on 2019-11-17
> **dragonfly41 said:**
> Do you have any local devices which might cause spikes on mains supply? This is a long, long shot.
I don't think so, but there is construction going on where I'm located at. I think the problem started around the same time as the construction. I could eliminate this possibility if I buy a UPS, right?

> **dragonfly41 said:**
> 
[Further thought] Did you take your monitor to the workshop or only the desktop (with any items missing)?
I only took the desktop.


I did the memtest separately on 6 RAMs.

2 of them completed 3 runs without any errors.

1 restarted maybe 5 seconds into the memtest.

3 didn't boot the computer at all (not even to bios, the screen was completely black the whole time).

After the tests I put the two good ones in and booted up the computer, but now it keeps on restarting. Either after 1 seconds or so (I can see the fan turning off and on) or just when the BIOS is starting to show up.

EDIT: [Saw additional replies] My old PSU failed recently and I bought a new one. Before that the computer worked fine for around 4 months in the same location.

---

### Post by dragonfly41 on 2019-11-17
I don't know if you read the tips in this thread (posted earlier).

[https://askubuntu.com/questions/880875/ubuntu-restarts-randomly-and-there-is-no-log-about-the-reason](https://askubuntu.com/questions/880875/ubuntu-restarts-randomly-and-there-is-no-log-about-the-reason)

e.g.  sudo apt install ipmitool

...

Also another thought ..
[https://en.wikipedia.org/wiki/Surge_protector](https://en.wikipedia.org/wiki/Surge_protector)

---

