---
title: "Will upgrading to 13.04 break current bumblebee setup?"
date: 2013-04-30
forum: General Help
---

### Post by gagsays on 2013-04-30
Hello everyone,
I was planning to upgrade my system to raring(xubuntu) but noticed that nvidia packages(but didn't see any bumblebee packages) will be installed in the process. That got me thinking, will it cause any harm to my near perfect bumblebee(stable) - nvidia(304) setup? I mean, can it mess up Xorg stuff? To me it feels like a situation similar to when an user directly installs official nvidia drivers on an optimus laptop and gets blank screen on next boot.

Thanks for your time.

---

### Post by Stonecold1995 on 2013-04-30
The upgrade broke Bumblebee for me, yes (I'm too lazy to try to get it to work again because only very rarely do I use my discrete GPU), but it did NOT break Xorg (i.e. my computer started fine after the next reboot, except for optirun didn't work).

---

### Post by gagsays on 2013-04-30
> **Stonecold1995 said:**
> The upgrade broke Bumblebee for me, yes (I'm too lazy to try to get it to work again because only very rarely do I use my discrete GPU), but it did NOT break Xorg (i.e. my computer started fine after the next reboot, except for optirun didn't work).
Wouldn't purging bumblee and reinstalling make it work again?

---

### Post by schragge on 2013-04-30
I'd say *removing* rather than *purging*. That way you'll keep your configuration.

---

### Post by gagsays on 2013-04-30
> **schragge said:**
> I'd say *removing* rather than *purging*. That way you'll keep your configuration.
Isn't the whole problem caused by messed up configuration files in the first place? Please correct me, if wrong.
And did you insinuate by your reply that upgrading will cause problem and removing bumblebee and re-installing will fix it.

Is there any way I can preserve this setup while upgrading?
If I am stuck on blank screen then what will be the exact step to correct the problem?

---

