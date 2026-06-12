---
title: "Something keeps resetting DPMS, How can I find out what?"
date: 2018-08-01
forum: General Help
---

### Post by karnival8 on 2018-08-01
I have this weird situation where my DPMS settings (standby, etc) keep getting reset to 0 and the computer never sleeps. I even went as far as making a cron to reset DPMS every 30 minutes so the machine doesn't stay up all night. This works most of the time.

Using Kubuntu with Nvidia drivers. 
I suspect it's an app that's doing it. 

Is there a way to find out which app is making changes to DPMS? There must be a log for this somewhere. 

I frequently run xset -q and a few times a day DPMS is reverted to 0. The cron fixes it eventually but without it, values would remain at 0. 

I have a suspicion on which app is doing it. Is it possible to revoke access to make changes to DPMS for this app specifically?

---

