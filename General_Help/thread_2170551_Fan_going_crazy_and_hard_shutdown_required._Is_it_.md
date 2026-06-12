---
title: "Fan going crazy and hard shutdown required. Is it the BIOS of my ThinkPad?"
date: 2013-08-26
forum: General Help
---

### Post by ShukatsuRonin on 2013-08-26
Hello,
 

 The situation: my laptop, a 2 year-old ThinkPad Edge 11, has been behaving strangely lately.  

 The fan is spinning full throttle non-stop. When I try to turn it off it gets stuck at “power down” (not sure of the exact wording) and I have to press the button for it to really shutdown.  

 After doing that I have to quickly remove the battery lest it would power on again.  

 When I turn it on, after the bios screen, it takes about 1 minute to reach grub whereas it used to take 1 or 2 seconds. The fan goes crazy right after the bios screen whether hot or not.

 Closing the lid doesn't really put it to sleep, the diode – on ThinPad Edges they're more a design element than anything and are always on – flashes faster than it used to and it actually freezes. A hard reboot is the only way I've found. 

 What I describe is common to Ubuntu and Windows.  

 

 The cause (?): I've flashed the bios on this machine more than once. The Fn keys along with the  sleep mode sometimes stop working. I've found on this forum that it's a bios issue.  

 When I went from 1.16 (86ET32WW) to 1.17 (86ET33WW) it appeared to have gone fine but the Fn were still unresponsive and forgetting about the sleep situation I closed the lid and left my computer for awhile. When I came back it seemed as though the fan had been off for a long time and my laptop was quite hot. After rebooting the situation described above started.  

 

 What I've tried so far: calling Lenovo but since my warranty has expired they couldn't care less. Checking my system with PC-Doctor that found that everything was fine. Downgrading the bios to 1.16. Using fan control programs (tpfancontrol and tpfanco) which used to work (tpfancontrol in Windows, I didn't know of tpfanco back then). Removing the battery after turning off the computer and pressing the power button. Opening the case and cleaning up the fan. Booting from a live-USB stick.  


 And nothing so far has worked, except for the Fn keys that respond again. I'm completely at a loss :(

---

### Post by bkline on 2013-08-26
If the BIOS offers any hardware tests, try running them.

---

### Post by tgalati4 on 2013-08-26
Sounds like a graphic chip delamination.  The GPU's run hot and warp causing shorts or dropouts.  The fan is running full speed because something is getting hot, right away.  Most thinkpads (I'm not sure how the edge is designed internally) have the CPU and GPU sharing the heatsink.  So if your GPU is getting hot, the fan will spin up, the bus will freeze requiring a hard reset.  

The fact that your issues are happening in both Windows and Linux would indicate a serious hardware problem.

You can try to open it up and replace the heat paste with a quality silver or ceramic paste and see if it will boot.  Otherwise donate it to a high school discus throwing team.

---

### Post by ShukatsuRonin on 2013-08-28
Thank you for your answers. 

As tgalati4 said, it seems to me like a serious hardware problem. Well, as far as I can tell. 

I need to get screwdrivers to open my computer and it's going to take some time because they are not readily available in my area. 

I'll keep you posted.

---

### Post by ShukatsuRonin on 2013-09-13
So the other day, a friend of mine with all the right tools helped me and we opened my laptop. He did all the work, actually. 

I was not completely pleased to see that the thermal paste looked ok when we removed the heat sink. We scrubbed the old one and applied a layer of the new one. Unfortunately, this operation had no visible effect: the situation is exactly the same (boot time, fan, shutdown). We also removed the battery of the clock but probably not long enough.

I've just tried flashing the bios to the latest version (forgot for a while where to find older versions) but again the situation hasn't changed one bit :cry:

---

### Post by tgalati4 on 2013-09-13
Well, you have done what you can.  It sounds like a motherboard failure or chip delamination.  Out of warranty means SOL--Seriously Out of Luck.  Donate it to a high school discus throwing team and make a youtube video out of it.

Have you done a web search to see if others are having the same problem?  If it is a design or manufacturing defect, then it will show up as failures for other folks.  If you have dropped it too many times, then I would suspect motherboard damage.

---

### Post by ShukatsuRonin on 2013-09-14
A not so extensive search proved fruitless. Not very common it seems. 

I did drop it once on a hard surface but that was about one or two months after purchase and it seemed ok until recently. I guess that could still be part of the explanation, though.

Damn, getting a new computer is going to be a pain in the rear.

---

