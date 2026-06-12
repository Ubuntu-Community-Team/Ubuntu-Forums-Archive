---
title: "Got latest 7.1.0 updates, now ntp doesn't work"
date: 2008-05-31
forum: General Help
---

### Post by stevecoh1 on 2008-05-31
Earlier this evening I took the latest Ubuntu 7.1.0 updates.  I suspect that's relevant because I never remember seeing this problem before this evening, but I'm not 100% sure of its relevance.  

Now my clock doesn't work.  It's set for ntp.  It shows the time as 5:23 pm, actually it's 10:23 now.  It is not set for UTC.  My timezone is America/Chicago and is correctly set, which should be five hours behind UTC.  Instead, time is showing up as 10 hours behind UTC.  It's almost as if some application is adding the timezone adjustment (-500) twice.  I've tried several different ntp servers, doesn't make any difference.

Has anyone experienced this know what is going on here?

Restarting the system has not helped.

---

