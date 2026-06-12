---
title: "No Audio"
date: 2015-04-09
forum: General Help
---

### Post by ronbrooks on 2015-04-09
I have had no sound for about month but what I found was the /etc/audio file was not right.  I was audio:x:29:svxlink,ronald,pulse and it should have been audio:x:29:pulse.  After I made the change and rebooted the system all was Okay.

I hope this will help someone else with the same problem.

---

