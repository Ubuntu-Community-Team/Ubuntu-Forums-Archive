---
title: "Xubuntu speedup"
date: 2007-01-10
forum: General Help
---

### Post by seuaniu on 2007-01-10
Hello all.  I recently acquired an ancient compaq 1274 laptop, and just got around to installing xubuntu edgy on it.  it features a 360Mhz AMD k6 processor, and a whopping 64MB of memory.  I'd like to know if anybody knows of any tricks to speed things up a bit, as the responsiveness is pretty bad.  On default install it doesn't start up any services that look to be "frivilous".  I've shut off cupsys, and after my update finishes I'll get rid of a couple of the virtual terminals to free up some memory.  After that, I'm at a bit of a loss as to what I can get rid of without seriously screwing up xfce.  Any ideas?  Thanks in advance.

---

### Post by meng on 2007-01-10
Of course the "obvious" solution is to go for fluxbox or icewm rather than xfce.
[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by seuaniu on 2007-01-10
That would definitely work, but I like xfce, and if there's a way to slim it down a bit, I'd like to keep it.  I have a fluxbuntu iso on my main machine that I'll burn and try out if I can't get xfce under wraps.  My main concern is that my wife and kids are used to gnome, and xfce's default layout is similar enough that they probably wouldn't even know that there was something else installed.  If I were the only one using it, I'd be fine with dsl or puppy, or just a terminal if it came to that.

---

### Post by Tazix on 2007-01-11
You'll have to do some Googling, but I suggest using xvesa (TinyX) instead of xorg for a 64MB machine, like DamnSmallLinux uses for it's Xserver.

Xorg is a major resource hog by comparison.  This will also eliminate any propriatary video drivers (if you loaded those), and rely on VESA only... which most video cards (even old ones) support.  Even Fluxubuntu with Xorg wouldn't save you that much RAM.

It's still going to be a bit slow.  Minimum of 128MB of RAM is pretty much a must.
Maybe you can pick up a cheap / used stick of 64MB and avoid the hassle of changing the Xserver.

I don't know any "how-to" off the top of my head, which is why you'll need to do some Googling.

-Taz

---

