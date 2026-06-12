---
title: "Not enough swap to hibernate."
date: 2008-07-08
forum: General Help
---

### Post by Birchlabs on 2008-07-08
Decided to leave this Eee PC with a swap partition, since it didn't work too desirably when I used it without one. Used the 'hibernate' feature, and it complained that there wasn't enough swap space. How do I allocate more?

Also, while I'm here, what's the difference between suspend and hibernate?

---

### Post by sdennie on 2008-07-08
You would have to resize your paritions to make room for more swap space.  However, if possible, it might be easier to just use suspend instead.  

Suspend just turns off the machine except for the ram.  This uses very, very little power (most machines are probably around 1-5% battery per hour) and makes the machine resume in a few seconds when you turn it back on (or, for many machines, open the lid).  

Hibernate stores the contents of the RAM to disk (swap) and when you turn it back on, it reads that information and puts it back into RAM.  While hibernated, the machine uses no power but, it can take a long time to both hibernate and resume from it (probably negating any power savings benefits depending on how long you've left the machine hibernated for).

---

