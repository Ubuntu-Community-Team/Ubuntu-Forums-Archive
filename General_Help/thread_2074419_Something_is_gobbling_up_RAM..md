---
title: "Something is gobbling up RAM."
date: 2012-10-21
forum: General Help
---

### Post by Makurosu on 2012-10-21
I haven't seen anyone else with this problem. I'm running Ubuntu 12.10 64-bit with 2GB RAM, and when I boot up something starts consuming RAM about about 1MB/sec until it reaches some sort of equilibrium at 1.2GB of RAM. Then it starts consuming swap a bit more slowly. The process thrashes the hard drive constantly for hours and makes the entire system pretty slow, obviously.

System Monitor only reveals that RAM is being consumed. No process shown seems to be holding onto it. I also ran gnome-system-monitor as root, which revealed nothing as well.

I'm not even sure this is a Quantal problem, because I am almost sure I saw it happening the day I upgraded from 12.04.

Anybody else dealing with this? Thanks guys!

---

### Post by The Cog on 2012-10-21
I'm not sire I would trust System Monitor. I've had the feeling it's hiding things before now, though maybe I just don't trust GUI things. I would suggest installing and using htop (a command-line app). You can list all the processes and sort on memory or cpu usage.

---

### Post by philinux on 2012-10-21
Yeah. I think there is a memory leak somewhere.  I'm seeing swap used too and something like 900 megs used and the rest cached out of 2 gig and that's with only Firefox running.

---

### Post by Makurosu on 2012-10-21
> **The Cog said:**
> I'm not sire I would trust System Monitor. I've had the feeling it's hiding things before now, though maybe I just don't trust GUI things. I would suggest installing and using htop (a command-line app). You can list all the processes and sort on memory or cpu usage.

Thanks for the tip! I think you're right. I tried htop, and it seems to be giving me a bit more information, though I haven't spent much time with it yet.

---

