---
title: "Slow boot from hibernation"
date: 2008-06-19
forum: General Help
---

### Post by milan.satala on 2008-06-19
I have a Fujitsu-Siemens laptop with 2GB RAM. My swap partition size is 3GB. I'm able to hibernate the laptop and wake it up properly if I have little memory used (~500MB). However I usually run a few memory-hungry application (firefox, tomcat, 2x eclipse) which make my memory usage go up to 2GB. I'm still able to hibernate and wake up but the problem is that it takes way too much time. It takes almost 3 minutes to boot back to KDE. I didn't measure the time in my XP installation but I think it was less than 1 minute. However this isn't the only issue. The computer is unusable for a few other minutes even after I get back to KDE. The thing is that the memory is still swapped. Let's say that my memory usage before hibernation was 1.9GB but after waking up it's only 600MB. Remaining 1.3GB of physical memory are still stored inside swap partition. This makes for some terrible swapping lag every time I click on anything.
The way I use my laptop makes hibernation a necessity for me and right now it's almost unusable. I would appreciate any ideas.

Milan

---

### Post by sdennie on 2008-06-19
Can you use suspend instead of hibernate?  Hibernate is unbearably slow for me as well.  If you can't use suspend, the only way to make hibernate faster (as far as I know) is to compile a custom kernel with TuxOnIce which supports compression of the hibernate image.

---

