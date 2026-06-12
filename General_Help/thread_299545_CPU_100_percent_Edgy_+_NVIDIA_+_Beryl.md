---
title: "CPU 100 percent Edgy + NVIDIA + Beryl"
date: 2006-11-14
forum: General Help
---

### Post by mjpoetic on 2006-11-14
It is weird, but if I have kiba-dock and beryl running on my desktop PC (with latest NVIDIA drivers), kiba-dock makes my CPU push 100% everytime.  Then, if I disable beryl (and use metacity or another window manager)...kiba-dock is fine.  No heavy CPU load or anything.  My desktop PC is running Edgy and I never experienced this problem in Dapper.  I don't know if it is because I was using XGL then.

Conversely, using kiba-dock on my laptop with Edgy, the onboard i915 intel graphics, and beryl runs fine.  I actually had to make sure I added the following line to my xorg.conf's Device section so it can run smoothly on the laptop:

```
Option     "RenderAccel"   "true"
```I tried adding this to my desktop PC's xorg.conf, but it didn't work (just trying anything I could think of that might help).  Speaking of help....I could use some!!! ;)

P.S.
I already posted this in the beryl forums...but just doing it here too

---

