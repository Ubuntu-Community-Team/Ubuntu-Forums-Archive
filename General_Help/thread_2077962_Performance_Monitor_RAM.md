---
title: "Performance Monitor: RAM"
date: 2012-10-29
forum: General Help
---

### Post by mike acker on 2012-10-29
Is the RAM use reported by the Performance Monitor accurate?

I don't think so: mine shows a steady line at 10% ( of 16GB )

yet if I eyeball the list of active processes it come out to a lot more than ~1.5GB,--
Audacity is using 1.1G, compiz has 1.1GB Firefox .758GB , Thunderbird .933GB
and the list goes on and on

do i need to fix my performance monitor ??

---

### Post by jerome1232 on 2012-10-29
Some of the pages in ram will be shared by processes, so say if firefox and thunderbird are sharing 150 mb's of their pages in ram, it gets reported as ram used by both processes.

Make sense?

---

### Post by jerrrys on 2012-10-29
Hay cowboy, how ya doing  :)

Take a look at ram in terminal to compare.

free -m

or 

top

---

### Post by mike acker on 2012-10-29
> **jerome1232 said:**
> Some of the pages in ram will be shared by processes, so say if firefox and thunderbird are sharing 150 mb's of their pages in ram, it gets reported as ram used by both processes.

Make sense?

1.5GB ram is all a system needs to be running ??  I'm getting 0B /swap

I know I meant to build a real hog of a computer but did I over do it?

the 4GB chips were $18.75 ea from NewEgg.  the M5A88-M board has 2 high speed memory slots ( the blue ones ) and 2 add-ons -- should I cut this critter down to 8GB ram ?

---

