---
title: "Strigi Daemon consuming unacceptable amount of CPU"
date: 2008-02-24
forum: General Help
---

### Post by Zeroangel on 2008-02-24
Hey all. Kubuntu user here! :KS

Sometimes when I log into KDE, the Strigi Daemon will start up in the background and cause everything to run much slower while it does its indexing thing (i think it usually uses up 25% of CPU and usually MySQL runs at the same time and causes up to ~40% of CPU). This is a noticable problem in games for example where my FPS will be halved and i'm forced to killall -9 strigidaemon, or renice it to 19 (its priority starts at 0)

Is there any way to configure strigi to run only during idle cycles, or to have it start out at a higher niceness level?

---

### Post by GuDoN on 2008-02-25
Can't find anoyone with the same problem, weird...

---

### Post by distratios on 2008-03-09
> **GuDoN said:**
> Can't find anoyone with the same problem, weird...

I just realised that I have the same problem. Have not fixed it yet ...

---

