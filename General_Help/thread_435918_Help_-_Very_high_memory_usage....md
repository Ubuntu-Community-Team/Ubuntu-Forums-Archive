---
title: "Help - Very high memory usage..."
date: 2007-05-07
forum: General Help
---

### Post by kevin79 on 2007-05-07
I installed Kubuntu on my Dell Latitude D820 last week. I have 2GB of RAM in my laptop.  Kubuntu is regularly using over 1GB of RAM een when I have very few applications running. Right now, I'm using 1,370,344 KB of RAM and I'm running KDE System Guard, Evolution (connecting to Exchange), Firefox, a terminal window, Open Office Calc, 2 Terminal Services clients and one instance of Konquerer. I don't see any reason that my RAM usage should be so high. Are there any tips that I can use to get my memory usage down?

---

### Post by rai4shu2 on 2007-05-07
I think memory usage isn't a big deal once you get past the minimum (256 MB). You might want to worry more about Load averages, Swap usage, and/or Uptime (all this is nicely presented using htop).

---

### Post by ddaedalus on 2007-05-07
First things first. 1,3GB used RAM or +buffers +cache? Its completely normal to use all the RAM for +cache and +buffers. OTOH OpenOffice.org is quite a memory hog.

---

### Post by kevin79 on 2007-05-07
> **ddaedalus said:**
> First things first. 1,3GB used RAM or +buffers +cache? Its completely normal to use all the RAM for +cache and +buffers. OTOH OpenOffice.org is quite a memory hog.

It is total used so +cache and +buffers.

---

### Post by mcduck on 2007-05-07
> **kevin79 said:**
> It is total used so +cache and +buffers.

then there's nothing wrong. Memory not used is wasted, so Linux uses all memory not used by applications as disk cache. Whenever some app needs more RAM, some cached files are dropped from memory.

To see how much your programs are using RAM, without counting in the disk cache, run 'free -m' in a terminal and lok at the +/- buffers/cache'-line.

---

### Post by rich.bradshaw on 2007-05-07
Linux uses as much meroy as it can so that is is actually useful - why pay for 2GB memory if you don't want it being used?!

---

### Post by nanonomic on 2007-05-07
well if you want more ram free you probably (BOTTOM LINE) dont want to have Konqueror open


it takesup a LOT of memory.  also if you really want minimal RAM then you should consider using Fluxbox.

---

