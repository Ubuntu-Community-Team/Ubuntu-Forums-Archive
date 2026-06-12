---
title: "Sound and Mouse are Choppy When System Is Under Load"
date: 2007-10-31
forum: General Help
---

### Post by pyro_xp2k on 2007-10-31
In Ubuntu and several other distributions, whenever the system is under load, the sound and mouse start getting choppy and I was wondering how I could fix this because some music programs and some of the heavier games I have like 'Second Life' and any sound application I have open when I decide to go do something else or something happens in the background get affected by it.

I've tried optimizing and recompiling the kernel and setting the preemptive option to 'Low-Latency Desktop', but I still get the choppiness under load.

Whenever I was using Mandriva, I never had any problems with the choppiness no matter how heavy a load the system was under, but I want to keep Ubuntu (since it has the largest software repository I've ever seen and I hardly ever have to compile anything. :P).

---

### Post by pyro_xp2k on 2007-11-01
*[thread bumped]*

---

### Post by pyro_xp2k on 2007-11-10
Never mind, I figured out the reason.
Apparently it had something to do with the scheduler I was using because when I changed it from 'elevator=cfq' to 'elevator=deadline' the jerkiness died down substantially.

---

