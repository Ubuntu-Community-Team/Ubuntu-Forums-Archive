---
title: "Problem booting Ubuntu 7.10"
date: 2007-11-29
forum: General Help
---

### Post by seamusandboo on 2007-11-29
Hi,

I wonder if somebody can help me with this problem I'm having. I recently received my copies of Ubuntu I ordered, both 32-bit and 64-bit versions. Everytime I try to boot from the CD, it loads the bootloader, then it shows the splash screen. When it starts loading the desktop, I see the orange background with the cursor and I hear the logon sound and then, all of the sudden, my screen goes blank and my monitor goes on stand by. It happens everytime. I already tried booting with all kinds of different resolutions to see if that's the problem, but that did not help. I also tried booting in safe graphics mode, but it doesn't work either. Only this time instead when the monitor goes blank it doesn't go on stand by, it only shows a black screen. This problem happens in both 32-bit and 64-bit versions of Ubuntu 7.10. Here goes my system specs:

Processor: AMD Athlon 64 X2 Dual Core 5600+ 2.8Ghz
Motherboard: Biostar T-Force 550 SE
Video Card: EVGA GeForce 8600GT 256MB
Memory: 2GB (2 x 1GB) G.Skill DDR2-800
Sound: Creative SB Audigy 2 ZS
HD: Seagate Barracuda 200GB
Monitor: Samsung SyncMaster 205BW

If anybody has any ideas of what's causing these problems I'd appreciate to hear them.

Thanks,

---

### Post by helix on 2007-11-29
Can you post your Xorg configuration for us?

---

### Post by seamusandboo on 2007-11-29
I'm not sure how to do that. My guess it's what the default xorg configuration for ubuntu is because I'm booting it from the CD, it's not installed in the hard drive.

---

### Post by discoade on 2007-11-29
I don't know if this is any help as im new to ubuntu !

When i did an install of xp once i had a similar problem. the graphics driver was launching in to higher refresh rate for my monitor 85htz so the monitor was shutting down! (LCD)

i had to startup in safe mode and drop the refresh rate to 60htz

i don't know if this applies in ubuntu though :confused:

---

### Post by seamusandboo on 2007-11-29
Yeah that does make sense, as my monitor only supports 60 Hertz, as far as I know. Ubuntu might be changing it to something else. I'm not sure how to set the refresh rate though but I'll look it up. Thanks for the hint.

---

### Post by seamusandboo on 2007-11-29
Yeah the more I mess with it the more likely it seems to me that Ubuntu is setting some default refresh rate that's out of range of my monitor and that's what's causing it to go to stand by mode right after booting. The only thing is, I'm not sure how to force Ubuntu to start with a certain refresh rate. There must be some parameters you set at the CD boot screen to force it to use certain refresh rate, but I'm not being able to figure out what it is. Does anybody know how to do that?

Thanks.

---

### Post by discoade on 2007-11-30
long shot...  do you now anyone thats got a crt monitor you could borrow for 10 minutes? try booting with that plugged in? \\:D/

---

### Post by kurian on 2007-12-27
i do have the same problem did you got any solution to change the refresh rate ....????
> **seamusandboo said:**
> Hi,

I wonder if somebody can help me with this problem I'm having. I recently received my copies of Ubuntu I ordered, both 32-bit and 64-bit versions. Everytime I try to boot from the CD, it loads the bootloader, then it shows the splash screen. When it starts loading the desktop, I see the orange background with the cursor and I hear the logon sound and then, all of the sudden, my screen goes blank and my monitor goes on stand by. It happens everytime. I already tried booting with all kinds of different resolutions to see if that's the problem, but that did not help. I also tried booting in safe graphics mode, but it doesn't work either. Only this time instead when the monitor goes blank it doesn't go on stand by, it only shows a black screen. This problem happens in both 32-bit and 64-bit versions of Ubuntu 7.10. Here goes my system specs:

Processor: AMD Athlon 64 X2 Dual Core 5600+ 2.8Ghz
Motherboard: Biostar T-Force 550 SE
Video Card: EVGA GeForce 8600GT 256MB
Memory: 2GB (2 x 1GB) G.Skill DDR2-800
Sound: Creative SB Audigy 2 ZS
HD: Seagate Barracuda 200GB
Monitor: Samsung SyncMaster 205BW

If anybody has any ideas of what's causing these problems I'd appreciate to hear them.

Thanks,

---

### Post by janarene on 2007-12-27
Ok, here's my guess at the problem... only because it happened to me with a PC that had a slow CD drive.  Same condition - screen went blank, monitor hit standby after booting from the CD.  The solution?  Well - there really wasn't one.  It took the desktop so long to come up that the screen saver or power saver routine kicked in.  All I had to do was shake the mouse and click a mouse button or keyboard key and the desktop was right there waiting for me.

---

