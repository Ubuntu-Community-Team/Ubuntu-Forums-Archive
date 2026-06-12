---
title: "Help, bring back partition"
date: 2007-04-25
forum: General Help
---

### Post by themerchant on 2007-04-25
I deleted my windows partition happily, (now that I can use wine really well), I just have a question, how can I add that partition that was deleted to my ubuntu partition.

---

### Post by tyler_roach on 2007-04-25
Download and burn the gparted liveCD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Boot from it, and when you get into gparted, right-click on your windows partition and choose delete. Then, right-click on your ext3 partition and choose resize. Stretch it until it covers what's remaining, then choose "apply".

---

