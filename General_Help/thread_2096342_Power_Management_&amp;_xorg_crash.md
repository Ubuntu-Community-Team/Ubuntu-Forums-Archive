---
title: "Power Management &amp; xorg crash"
date: 2012-12-19
forum: General Help
---

### Post by nhkim on 2012-12-19
Hi. 

I'm having a bit of issues with the power management settings and constant crash reports. 

I'm running Xubuntu on a Thinkpad x230 and I set my power setting to leave everything on (display, computer) when idle. However, the display keeps going off when I leave the laptop idle for about five minutes. 

Also, when I close the lid and wake from suspend and sometimes when I reboot, I keep getting getting these crash reports. The only info I get is that it's xorg. I don't even know what that is and nothing seems to be wrong with the computer.

---

### Post by Pjotr123 on 2012-12-19
Disable suspend like this:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)
(item 7, right column)

Also, check your screensaver settings.

---

### Post by nhkim on 2012-12-19
> **Pjotr123 said:**
> Disable suspend like this:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)
(item 7, right column)

Also, check your screensaver settings.

Wow. I feel stupid. I didn't even bother looking at the screensaver settings. Thank you.

Also... Should I disable suspend and just shut down all the time? I don't particularly mind, but I also want to know what the xorg crashes are and how to fix it if possible.

---

### Post by nhkim on 2012-12-20
It looks like I'm getting xorg crashes randomly while using the computer as well. 

In the details the title is:
Xorg crashed with SIGABRT in raise.

I can ignore the problem, but I want to make sure it isn't something significant.

---

### Post by Pjotr123 on 2012-12-20
I advise to report this on Launchpad. There have been several similar bug reports in the past, although they have been marked "fixed"....
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/933504](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/933504)

Note the last comment in the thread.

---

