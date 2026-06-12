---
title: "System freezes"
date: 2012-11-23
forum: General Help
---

### Post by completepete on 2012-11-23
Hi 

I had been having smaller system freezes for a long time. When the cpu idled every process would stop, until I moved the mouse or pressed a key.

I fixed this by adding "nohz=off" to grub config.

I don’t have these small freezes anymore. Instead I have a more serious problem. Now the whole computer randomly locks up. Like a 100% freeze, 3-4 times a day.

I tried adding "nolapic_timer" too, with similar results.

As i understand, it has something to do with the clocksource. And by adding "nohz-off" I force it to disable the tickless timer.

specs:
ubuntu 12.04

intel T8300
nvidia 8600gt

I hope you can help me find some sort of solution.
Thanks.

---

### Post by howefield on 2012-11-23
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2086676](http://ubuntuforums.org/showthread.php?t=2086676)

---

