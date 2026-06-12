---
title: "Noob with several starter questions"
date: 2007-06-16
forum: General Help
---

### Post by bronze on 2007-06-16
Hiya,
for a month or so I've have a dualboot with PCLinuxOS and Win XP, to get a feeling of how linux is. I tried Beryl, and after some fixing around, I got it to work. What surprised me was how smooth is was. It was almost like the system was running better WITH the 3D effects than without.

However, now with my freshly formatted PC, and Ubuntu, things are quite different. I haven't tried to enable the 3D cube yet (I used it in Beryl), but right now Compiz isn't really as smooth as I want. I've tried dragging the windows around (to check wobbly windows), and it's easy to spot the difference.

My question: What do you think is different this time, and why is it like this?

My guess is that it has something to do with the setup, perhaps something with native hardware acceleration (which I wanna use, but I can't find out how to control compiz).

And yes, I have installed the nvidia drivers (via system -> administration -> "Driver manager"

My setup:
aSUS A8N-SLi Premium
AMD Athlon64 X2 4400+
twinMOS 2x1GB DDR-DIMM 3200
Gainward GeForce 7900GTX 512MB DDR3
Samsung SpinPoint S-ATA2 250GB 7200RPM


And another thing:
Is there any way to set the resolution to 1280x1024 and the refresh rate (Hz) to 72? Without drivers I have 75 and 85. With the drivers I have 52, 66 and 67.

---

### Post by moore.bryan on 2007-06-16
> **bronze said:**
> Is there any way to set the resolution to 1280x1024 and the refresh rate (Hz) to 72? Without drivers I have 75 and 85. With the drivers I have 52, 66 and 67.
[i]for this, have you tried: ```
sudo dpkg-reconfigure xserver-xorg
```
i can't speak to the rest of your problems; i have a low-end machine and a crappy graphics card, so i wouldn't go near beryl with a 10-foot pole.[/i]

---

