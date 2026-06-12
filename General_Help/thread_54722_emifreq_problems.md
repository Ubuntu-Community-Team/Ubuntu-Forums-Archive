---
title: "emifreq problems"
date: 2005-08-05
forum: General Help
---

### Post by raghav_p on 2005-08-05
I have a 1.5Ghz Centrino and have powernowd installed.

I installed the emifreq-applet on a panel and it worked UNTIL I rebooted my computer.

Then it pops up a message saying that I don't have the correct daemon running to change frequency. But I KNOW I have powernowd running because it keeps changing my frequency.

I thought it might be because emifreq started before powernowd so I changed emifreq priority to 0 to make sure. No help.

Any ideas?

---

### Post by leech on 2006-01-31
The problem is that you need to RAISE the priority, not lower it.... hope this makes sense.  It loads the things from 0 on up.  So if you set the load priority to 0 it tries to load it before everything else.  Just use bum to raise the number to 22.  It worked here just fine.

Leech

---

