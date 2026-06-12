---
title: "[SOLVED] Odd readings for my Core 2 Duo T7250"
date: 2008-01-28
forum: General Help
---

### Post by NovaAesa on 2008-01-28
I just got a new laptop with a Core 2 Duo T7250 in it but the processor cores don't seem to be running at full capacity. It almost seems as if the two cores can only sum up to 100%. E.g. if one core is at 80% then the other can only be at 20%. Here's a screen shot of system monitor to illustrate while I was running oggenc. Is this what should normally happen or do I have to do some tweaking to get full performance?

---

### Post by ~LoKe on 2008-01-28
79.2 + 27 = 106.2  So it's definitely not just a total of 100%.  It's trying to split the load across both processors.

---

### Post by steveneddy on 2008-01-28
Most of the applications will only use one processor, and the Linux kernel will split the load between both processors to even out the load.

This is normal behavior.

---

### Post by NovaAesa on 2008-01-30
Thanks for the replies everyone.

You are right about 1 programme only being able to use one core. If you are interested I got both cores to run at full capactiy at the same time though. I just ran oggenc and DVDShrink through VBox.

---

