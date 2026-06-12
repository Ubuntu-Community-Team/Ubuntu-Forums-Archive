---
title: "Ubuntu failed to boot"
date: 2007-11-28
forum: General Help
---

### Post by shakil on 2007-11-28
Hi,

I have following problem:
During boot, just right before the gui start, ubuntu throws me to the terminal saying something like: "kinit: no resume image, doing normal boot..." and after that nothing is happen (I've waited for about 10 minutes). The only shortcut which is working - CTRL-ALT-DEL (which just restarts PC).
I have 2 guesses, which can be source of such behaviour:
1) later today I had problems with electricity and of course computer was shut down incorrectly, however I've booted normally after that, without errors. 
2) Just right before this error I was playing around with ALSA driver to make sound in the Flash plugin work.

Most likely, the last action is main reason of my problem.
Could pls, someone help me with this one or at least give me some directions?

I'm using 64-bit Ubuntu 7.10.

P.S. Recovery mode is working without any errors (even sound in flash is finally started to work :))

---

### Post by shakil on 2007-12-01
I have solved this problem, so if someone is interested here is the solution:

It turned out, that gdm is depends on alsa-utils and when I removed alsa, than of course gdm was also removed. So in recovery mode I just installed gdm and ubuntu finally started.

---

