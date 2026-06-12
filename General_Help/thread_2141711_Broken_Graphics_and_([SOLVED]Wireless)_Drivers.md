---
title: "Broken Graphics and ([SOLVED]Wireless) Drivers"
date: 2013-05-03
forum: General Help
---

### Post by Carlington on 2013-05-03
Alright, let's see if I can run through all of this. Today has been rough.

So a while ago, I install the Steam for Linux beta, and later moved to the full client. Much to my dismay, I found that the Source engine, the basis for many popular Valve titles, relies on OpenGL 1.3, and my i3 Ironlake Mobile graphics chipset does not support OpenGL 1.3
With much help from people in both the Steam dev team and the Intel dev team, a workaround has been found for this problem. This workaround was included in the Mesa daily build that was pushed to the xorg-edgers PPA earlier today. Now, I don't have much experience with bleeding-edge PPAs, but the process seemed relatively simple, and so I decided to switch from the x-swat-updates PPA to the xorg-edgers. What I failed to do, was disable the x-swat-updates PPA, and I believe this may have been the root of my issues so far. When I attempted to pull the updates from the new PPA, it updated me from kernel 3.2.0-41 to kernel 3.5.x, which broke horribly. So, I booted back into 3.2.0, and manually downgraded the kernel, keeping all of the Mesa updates.
This caused further issues, so I decided to start over, running ppa-purge for both x-swat-updates and xorg-edgers. This reverted me to the 3.2.0 kernel, and removed all of the Mesa updates, so as to fix any possible issues that had been caused since the start of this whole affair. So, the first issue I'd like to address is why any of this happened. Why did kernel 3.5 break my system?

However, somewhat more pressingly, downgrading the kernel has broken my wireless driver. This has happened before, I am affected by the known issue with certain Ralink wireless cards, so I tried to fix it in the way I usually do. Only, this time, it isn't working. So, with some urgency, is anybody able to help me fix my wireless driver, and, after that, with somewhat less urgency, help me set up the xorg-edgers PPA properly?

Any help would be very very much appreciated, and you have my eternal thanks in advance.

EDIT: I fixed the problem with my wireless driver. Searchers: I deleted the directory /etc/modprobe.d/Wireless/RT5390STA and then re-created it, and copy-pasted the file RT2860STA.dat into it without modification. I hope this can help.
This leaves me only with the first problem, making xorg-edgers work. I feel like that might be better suited to a different section, though?

---

