---
title: "libesd-alsa0 and SDL apps"
date: 2005-04-18
forum: General Help
---

### Post by NeoChaosX on 2005-04-18
Okay, awhile ago I was complaining about have sound synching problems with SDL games. After reinstalling Ubuntu, I seemingly fixed it, but when I tried to set up ALSA sound mixing again, the sync problem remanifested itself.  However, I found that the sync is caused by having libesd-alsa0 package, instead of libesd0, installed. Other than that, ALSA works wonderfully.

Now I have two questions:
1) Is there anybody else who has had audio syncing problems with SDL apps when libesd-alsa0 is installed?
2) Is there a fix for this, or do I have to keep on relying on ESD for proper sound mixing? I'm not a big fan of libesd0 because music and video playing have noticable lag when starting and stopping with it installed.

Much thanks in advance.

---

