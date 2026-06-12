---
title: "battery time decreased with Compiz"
date: 2008-05-05
forum: General Help
---

### Post by finite9 on 2008-05-05
Im using Hardy heron, but the effect is the same no matter which version of Ubuntu I use:

When desktop effects are enabled, battery time is severely decreased.  Anyone else have the same issue?  Are there any ways to stop it taking so much juice, like changes in xorg.conf parameters?

I like Compiz, but it really is not worth the extra juice, so I run without and check each new version of Ubuntu that is released to see if it is better.  Maybe most people use Compiz on desktops and dont notice this?

---

### Post by Rocket2DMn on 2008-05-05
That is normal, compiz just takes a lot more processing power in your cpu and video card which drains your battery faster.  I always keep compiz disabled when I'm on battery, you can just enable metacity
```
metacity --replace &
```
Then back when you want compiz again, just run
```
compiz --replace &
```
I made launchers in my panel for those (don't need the &), though there is also an applet now in Hardy called fusion-icon which is available in the repos and can be enabled from Application->System Tools->Compiz Fusion Icon.

---

### Post by finite9 on 2008-05-05
neat.  thanks for the tip.

---

