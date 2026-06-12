---
title: "Sluggish workstation, cpu usage 30% even when idle"
date: 2007-07-17
forum: General Help
---

### Post by rzei on 2007-07-17
Hellou everyone!

Not long ago I noticed following problem when using Kubuntu 7.04; top tells me that cpu use is continuesly something along 20 %si to 30 %si when idling. I find this rather strange and it seems to make my desktop use (web browsing etc.) sluggish.

My system is about:
[LIST]
[*]Athlon XP 1800+ with 768MB RAM
[*]320GB IDE-hardrive
[*]NVidia 7600GS with the latest nvidia corporations binary X11 driver (installed using nvidia installer)
[*]Sound"card" is based on ac97 codec integraded on motherboard
[/LIST]

If anyone had any clues how to try tracing %si (soft interrupt) usage I would greatly appreciate. So far I've been that it could be caused by the soundchip, but it doesn't explain why cpu usage hovers around 20...30% when idling, not playing any music what so ever. Neither can nvidia driver be blamed for it, as open source driver doesn't lower cpu usage.

Under load I've noticed that %si goes down to 10...20% but never under about 10%.

---

### Post by rzei on 2007-09-13
Replying myself, but I've found out by removing modules one (or few) at a time that the main culprit is module "processor" which is part of the ACPI power management.

Luckily for my system it is completely unnecessary module.

Also, I found out that "processor" itself doesn't cause 20-30% si, but it's more like "triggered" by networking intensive applications such as KTorrent.

I haven't tried out anything other than the two latest stock kernels (and modules) -generic and -lowlatency, nor am I planning to try more recent Linux kernels as I do not have the time.

---

