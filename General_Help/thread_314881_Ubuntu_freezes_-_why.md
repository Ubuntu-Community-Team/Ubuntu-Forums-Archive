---
title: "Ubuntu freezes - why??"
date: 2006-12-08
forum: General Help
---

### Post by Kobussie on 2006-12-08
Hi all!

I'm running ubuntu 6.06 since a few month without major problems. But the last week my system freezes a couple of times a day. It's a complete freeze:
mouse & keyboard don't function; screen stays unchanged. I can't do anything but a push the reset button - then the systems starts up without problems.
I looked at the log-files: can't see anything extraordinary; only that i restarted..
Last time i ran "top" in a terminal; i could not see anyting strange there..:-k 
So this could be a hardware problem; but how do I find out??

Any help will be welcome!!

---

### Post by wpshooter on 2006-12-08
As a first step you might want to run the Ubuntu utility that is comparible to chkdsk for M/S windows.

I would do that and then watch it for a while and see if freeze continued.

However, I sort of suspect hardware problem.  Might want to reseat all components (including memory) that are connected on the motherboard.  You may want to run memtest86+ to test memory integrity.  After that I would suspect either bad power supply or overheating.

Good luck.

---

### Post by Kobussie on 2006-12-08
Thanks for answering my question!

Can you (or anyone else) tell me more about:
> to run the Ubuntu utility that is comparible to chkdsk for M/S windows?
Where do I find it?

CPU / mb temperature can not be the problem here: current reading (with lm-sensors) MB 22°C; CPU 29°C.

---

### Post by wpshooter on 2006-12-08
Let me see if I can find some references to it and I will post a link or maybe someone else knows a help reference right off-hand.

---

### Post by wpshooter on 2006-12-08
Do an advanced search of this forum on **FSCK** or check disk or chkdsk.

---

### Post by Kobussie on 2006-12-08
O.k. thanks!

I see that fsck is the command I need. But I'll have to do that with the filesystem not mounted (warning from fsck) So I think I'll try it from my Suse-system on the same disk. I'll let you know...

P.s: my up-time is now 1h:45! Not bad compared with earlier today!:D

---

