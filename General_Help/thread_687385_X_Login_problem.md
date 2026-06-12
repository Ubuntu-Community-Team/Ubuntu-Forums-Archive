---
title: "X Login problem"
date: 2008-02-04
forum: General Help
---

### Post by harvodan on 2008-02-04
Hi. I recently tried messing about with sysv-rc-conf, in an effort to speed up my ubuntu feisty boot time. I'm not sure if this triggered my problem, but it seems likely.

My problem is that recently, when X starts, the NVIDIA splash screen shows, and a black screen with a mouse cursor shows up. This lasts about 30 seconds, after which X seems to die, and then the splash screen shows again, and X restarts. At this point I can finally log in. I think it might be trying to launch X on two virtual displays, but for some reason, doing it on one twice?

I will post any config files, logs, etc, that might be helpful, if only someone will tell me what to put up here. Thanks in advance.

Also, I'm running an NVIDIA 8800 gts, an am2 6000 cpu, (32 bit linux) 2 gigs of ram.

P.S, I consider this annoying enough to re-install for, it's really bugging me. Thanks in advance for any help.

---

### Post by jken146 on 2008-02-04
Did you make a backup of that file before changing it?  If you did, restore your backup and see if the problem goes away.

---

### Post by harvodan on 2008-02-04
> **jken146 said:**
> Did you make a backup of that file before changing it?  If you did, restore your backup and see if the problem goes away.

No such luck. I looked in Snypaptic, and there is no single file to delete or overwrite in this instance, so that option seems likely to not go anywhere. Thanks anyway.

---

### Post by harvodan on 2008-02-05
I've switched from gdm to kdm, there's no such lag there. Everything seems to work well with kdm, so I'm definitely thinking it's a weird gdm problem. I'm going to hunt down and remove all files associated with gdm and reinstall, and see how that goes.

---

