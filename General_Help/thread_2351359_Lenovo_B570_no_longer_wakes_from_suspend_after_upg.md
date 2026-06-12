---
title: "Lenovo B570 no longer wakes from suspend after upgrade"
date: 2017-02-02
forum: General Help
---

### Post by Speedoo on 2017-02-02
Hi all,

I've been working on this for several weeks now, but haven't had any success.  I'm running an older Lenovo laptop, model B570.  I had been running a 32-bit OS since I bought the laptop (I think it was 2008?)  This year I decided to "upgrade" to the 64-bit system while installing Ubuntu 16.10.  Everything works fine, except I can no longer use the suspend feature of my laptop.  When I close the lid, the screen apparently goes black but the power stays on.  When I open the lid, nothing I do will wake the computer up.  I have to manually power it off, then restart it.  I had experienced this before with other laptops running Ubuntu, so was happy that the Lenovo actually responded to the suspend and hibernate commands.  Another anomaly I've noticed is that, when I power down the laptop, it doesn't turn off.  It hangs at "Reached target shutdown."

My questions are as follows:  Could these two problems be related?  Is this a function of the new 16.10, or did it result from switching from 32-bits to 64-bits?  If I find another linux distribution that works, would I be able to insert my Ubuntu home directory to preserve my data and settings?

Sorry I'm not more informed about the workings of linux; I'm happy to supply any screenshots or info needed to help resolve this problem.  Thanks!

---

### Post by Gervase_Markham on 2017-05-31
Hi,

I also have a B570 and I just tried suspend with Ubuntu 14.04 32-bit and 64-bit, and 16.04 32-bit and 64-bit, by booting from USB. Only 14.04 32-bit works; all the others fail to suspend properly, with symptoms as noted above. So it seems like the problem is _both_ the 64-bitness and 16.04 - switching to either makes the system no longer work.

So I guess I'll just have to reinstall 14.04 32-bit :-(

---

### Post by johnnyzee on 2017-06-10
I have a System76 64-bit machine running 16.04 that does the same thing. It is maddening. Is there no fix?

---

