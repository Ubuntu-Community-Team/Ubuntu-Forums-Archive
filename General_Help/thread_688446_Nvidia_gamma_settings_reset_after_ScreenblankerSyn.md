---
title: "Nvidia gamma settings reset after Screenblanker/Synaptic"
date: 2008-02-05
forum: General Help
---

### Post by Rumpanzle on 2008-02-05
Whenever I install via Synaptic (+updates), or the screenblanker was in action my gamma values of the nvidia-settings get reset. If I open nvidia-settings from the menu afterwards they get reapplied correctly. This is annoying, because my (old) monitor is off its limit with its build in hardware color correction, so I have to do additional gamma settings in the nvidia settings. All tips about .nvidia-settings-rc doesn't work, because I don't log off, or restart. I don't want to have "nvidia-settings -a" running in a cron job every ten seconds.

Thanks!

---

### Post by GraveyardPC on 2008-02-06
I have a similar problem. Every time power management kicks in and puts my monitor to sleep my color correction settings are lost. I have "nvidia-settings -l" on start-up, but like you said, it happens during normal use -- not after a restart.

---

### Post by syndr0 on 2008-02-21
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
[http://www.tech-geeks.org/contrib/mdrone/cron&crontab-howto.htm](http://www.tech-geeks.org/contrib/mdrone/cron&crontab-howto.htm)

i just tried using that.. it schedules tasks or w.e im not real good with this **** but ill find out if it works later on

---

