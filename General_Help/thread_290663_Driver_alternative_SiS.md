---
title: "Driver alternative SiS"
date: 2006-11-01
forum: General Help
---

### Post by Aurdal on 2006-11-01
I have an integrated graphics card on my SiS motherboard.

As far as I know, in Linux I only have two options when it comes to drivers for this, the VESA driver, and the SiS driver.

And well, both of them are very bad. The SiS driver makes vertical lines on my screen which are a symetric pattern of what should be where the lines are on the other side of my screen:

Suppose it's supposed to look like this:
```

|-----------------------|
|¤¤¤¤####""""!!!!|
|¤¤¤¤####""""!!!!|
|¤¤¤¤####""""!!!!|
|¤¤¤¤####""""!!!!|
|¤¤¤¤####""""!!!!|
|-----------------------|

```
Instead it looks like this:
```

|-----------------------|
|¤!¤¤"##"#"""!!¤!|
|¤!¤¤"##"#"""!!¤!|
|¤!¤¤"##"#"""!!¤!|
|¤!¤¤"##"#"""!!¤!|
|¤!¤¤"##"#"""!!¤!|
|-----------------------|

```
And as for the VESA driver, well it lags, a lot.

So, does anyone have any suggestions as to what I can do?

---

### Post by dannyboy79 on 2006-11-01
well I can tell you that I may have the same onboard graphics card 
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
Subsystem: Foxconn International, Inc.: Unknown device 0c56
Flags: bus master, medium devsel, latency 32
Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
Capabilities: [c0] AGP version 3.5

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
Flags: bus master, 66MHz, fast devsel, latency 64
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
Memory behind bridge: e8000000-eaffffff
Prefetchable memory behind bridge: d0000000-dfffffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
Flags: bus master, medium devsel, latency 0

and after some research and looking into this site, [http://www.winischhofer.eu/linuxsispart3.shtml](http://www.winischhofer.eu/linuxsispart3.shtml), I found that it wasn't possible to get DRI/3D/OpenGL per this statement: Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number. I figured it would be a hell of a lot easier to spend $40 and buy a GeForce 6200 and use the nvidia drivers so that I could have accelerated graphics. I can tell you that I am glad I spent the money and didn't waste the time trying to use the drivers that that site may have because my time is more vauleable then the many hours it would have taken me to figure it out and which it still wouldn't have been accelerated graphics. I couldn't even watch an .avi file without it pausing every once in awhile, it was the worst choice at a motherboard I could've bought! I am a newbie, I started using linux about 6 or 7 months ago, Ubuntu is my very first distro so you may know how to use what's on that website better than I know how. If you do figure it out, I know there are tons of people wanting this same solution so please post back you results and let us know if your graphics performance imporoved any with those drivers. thanks

---

### Post by Aurdal on 2006-11-01
Yeah, well I have an nVidia 6800XT, but thing is whenever I put it im my computer freezes after some time. Sometimes it can hold for a week, sometimes it's an hour, so...

Thanks for your reply though.

---

### Post by dannyboy79 on 2006-11-01
> **Aurdal said:**
> Yeah, well I have an nVidia 6800XT, but thing is whenever I put it im my computer freezes after some time. Sometimes it can hold for a week, sometimes it's an hour, so...

Thanks for your reply though.

well what drivers do you have installed when it does this? there are many different versions of the nvidia drivers, try the ones in the repo, then if it still crashes try the latest ones or older ones, I am sure you get it up and running. also, how do yo know it's your graphics card? what do the logs say after the freeze, syslog, xorg log, messages, kernel log?

---

### Post by Aurdal on 2006-11-02
I don't think it's a driver problem, it happens in Windows too, but then again I'm not actually sure if it's ever happened before I've installed any drivers. perhaps I should try again with the "nv" driver...

---

### Post by CatKiller on 2006-11-02
> **Aurdal said:**
> I don't think it's a driver problem, it happens in Windows too

It could be an overheating problem, or a power problem. Either of these would cause problems when you were asking it to do more work.

---

### Post by Aurdal on 2006-11-02
> **CatKiller said:**
> It could be an overheating problem, or a power problem. Either of these would cause problems when you were asking it to do more work.
I don't think it's heat because the card is the coldest thing inside the box, and it doesn't happen when I try to make it do more work, it can happen when it's not doing anything but displaying the screen saver or a webpage...

I'm now trying the card with the "nv" diver.

---

