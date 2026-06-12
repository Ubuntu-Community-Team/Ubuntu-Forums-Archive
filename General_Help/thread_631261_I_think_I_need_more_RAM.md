---
title: "I think I need more RAM"
date: 2007-12-04
forum: General Help
---

### Post by pajim17020 on 2007-12-04
I just got my ATI video card working properly and set up compiz fusion. Now everything is slow. When I scroll a window it lags. If I play a video its all jumpy and slow. I am not sure if the probem is lack of ram, cpu speed or video card. My computer is a AMD Athlon 1700 (1100mhz), 512 megs DDR RAM, ATI Radion 9550 agp card with 256 meegs of DDR ram on the card. If I open system monitor with nothing running my RAM is about 45% used. If I have a few windows open then its about 60-70% used. Right now it is at 61.8%. Do you all think more ram will help much or would it be a waste? I can put up to 1gig in this moboard.

---

### Post by nqsonk9 on 2007-12-04
Uhmm, I dont think there's a problem with hardware there. Compiz works fine even with 256mb and VGA card onboard. 

So, why dont you look for the xdriver for ATI and try to optimize the screen solution of your machine ?

If you think the system use more of your RAM than it needs to, do a ps or top check, kill some unused processes.

Tell me it works :)

---

### Post by banewman on 2007-12-04
You might need to find a better driver for your video card. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by -grubby on 2007-12-04
I don't see how that's possible since Compiz takes the stress off the CPU by drawing the screen with mostly your videocard....SO I'm guessing there is something wrong with your videocard drivers

---

### Post by defenestratos on 2007-12-04
In saying that I upgraded to a gig recently and I never use swap even when I indulge my bizzare multitasking addiction! My machine flies and I have no graphical acceleration. A bit ridiculous that OSs these day want a gig but there you are. Try the drivers and if that doesn't work the ram definitely will.

---

### Post by knutschr on 2007-12-04
I try again, because this was a real nightmare to me untill I found the solution:
```
sudo apt-get remove xserver-xgl
```

---

### Post by pajim17020 on 2007-12-04
I just spent 2 days installing and getting the ATI driver working it is version 8.42.3. I think that is the newest. I got it from ATI's sight. The restricted driver that ubuntu didn't work at all. I think you all are probably right about the driver. When the 3-D screen saver is up it flickers a bit now. If I disable the 3-D effects it work normal. I tried killing a few apps it might helped a bite but not dramatically. I wasn't sure what all was safe to kill.  How do I do a ps or top check?

---

### Post by pajim17020 on 2007-12-04
> **knutschr said:**
> I try again, because this was a real nightmare to me untill I found the solution:
```
sudo apt-get remove xserver-xgl
```

What does this code do?

---

### Post by knutschr on 2007-12-04
Bst way,I think:
```
sudo apt-get install htop

```
You can start it from System menu.
I have it running on a desktop with terminal and System Monitor too.
Very convinient :-)

---

### Post by pajim17020 on 2007-12-04
I disabled the compiz and noticed a couple of things. All lagging stoped the cpu usage dropped about 20% when playing a video. It was at 100% with a video playing with compiz enabled. The ram use dropped to about 30%. 3-D screen savers work with no flickering. So I'm thinking the problem is not the video card driver but the cpu is just to slow to keep up. This machine is 6 years old so I can't complain. I'll have to think about upgrading soon.:(

---

### Post by GlennW on 2007-12-04
I've been reading this thread with interest since I have a similar situation not altogether unrelated. My Gutsy box is as follows:

[INDENT]P4 1.6 Ghz
1 Gb RAM
80 Gb HDD
nVidia Geforce 6200 256 Mb
dual boot with XP[/INDENT]

I was having some performance issues and remembering the old adage that the best upgrade was more RAM, I added another 512 Mb. However, XP runs much better than it ever has but Gutsy is still plodding along, reliable as ever, but not taking advantage of the new RAM. I have compiz fusion installed with much of the eye candy but not everything since that causes too many delays. I have a CPU/RAM desklet so that I can monitor both. When apps are loading and processing the CPU is maxed out but the RAM has never risen above 30%. I don't mind a bit of wait time since it's an old mule but this seems like free horsepower that is going to waste. 

 One of the main reasons for migrating from XP was the performance issue. ***How can I avail of my new RAM to improve my performance?***

---

