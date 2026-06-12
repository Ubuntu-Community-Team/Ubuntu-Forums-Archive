---
title: "Suspend problems on Asus S301LP"
date: 2014-05-26
forum: General Help
---

### Post by Fallingwater on 2014-05-26
I've set up for another user a Win7/Ubuntu 14.04 (with Mate) dualboot on the titular laptop. Ubuntu pretty much works, I've just set it to use the proprietary video drivers and everything seems to be working fine. Everything, that is, except for suspend. 

If I do suspend it goes to sleep mode, but when I wake it up again the only thing that's responsive is the mouse cursor - no amount of clicking or typing actually does anything. After a few seconds even the cursor hangs, and I can hear the CPU fan ramp up. The system becomes completely irresponsive at this point - even ctrl+alt+f1 doesn't do anything, and the only solution is a hard reset.

How do I fix this?

---

### Post by Fallingwater on 2014-05-27
I have tracked the problem to the proprietary video drivers. If I use the opensource ones everything works fine, but the fglrx ones cause the abnormal behaviour. The fglrx-updates ones are even worse - it doesn't even go into suspend.

Is this fixable, or do I have to use the unaccelerated open drivers?

---

