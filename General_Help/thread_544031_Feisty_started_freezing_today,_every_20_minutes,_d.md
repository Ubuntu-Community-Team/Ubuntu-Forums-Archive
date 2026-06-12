---
title: "Feisty started freezing today, every 20 minutes, driving me crazy"
date: 2007-09-05
forum: General Help
---

### Post by wammin on 2007-09-05
After running Fiesty with almost no problems for months, my laptop started freezing frequently today. Everything locks up, the cursor does not move, and I have to do a hard power down, nothing else works. One time when this happened I was playing music, and the music froze in a loop at the same time the laptop locked up.

At first I thought it might be Firefox, or my truecrypt partition, or the sorta buggy Aptana IDE that I use often, but I was able to rule out those things by not using them and still experiencing the problem. I can't recreate the lock-up on demand, but it has been consistent all day and is beginning to drive me nuts.

Anyone know how I can try to get to the bottom of this?

I did install some updates this morning from the update-manager. I can't remember what they were. Is there a way to see a history of those updates? Maybe one of the new packages is causing the problem.

Are there any log files that might be helpful? I haven't found anything that indicates an error.

I appreciate any help or ideas.

---

### Post by llamakc on 2007-09-05
Run memtest and check your RAM.

---

### Post by wammin on 2007-09-06
I started memtest before I went to sleep, and it's been running for over 9 hours and passed 15 cycles with no errors or failures. I'll let it go a little while longer while I do some errands today, but I think it's safe to conclude that the memory is not the problem.

Could it be another hardware device that is failing? Any clue how I would track this down?

The laptop is still totally freezing up every 20 mins - 1 hour. Still, my only resolution is to hard power down and restart.

Any ideas are appreciated

---

### Post by Hallvor on 2007-09-06
Anything in your logs?

---

### Post by wammin on 2007-09-06
Nothing out of the ordinary in /var/log/messages. I see the normal boot / startup stuff, but there is nothing at all around the time it last froze.

What other logs should I check?

p.s. I'm pretty good when it comes to software stuff ... but hardware debugging is a little bit out of my comfort zone

---

### Post by oomingmak on 2007-09-06
> **Hallvor said:**
> Anything in your logs?
Why am I suddenly thinking of Gillian McKeith?

:???:

---

### Post by rsambuca on 2007-09-06
Do you have a cpu temp monitor installed?  If it is happening consistently it could be due to heat issues related to the cpu or even the gpu.

---

