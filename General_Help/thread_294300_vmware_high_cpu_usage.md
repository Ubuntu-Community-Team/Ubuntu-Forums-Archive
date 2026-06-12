---
title: "vmware high cpu usage"
date: 2006-11-06
forum: General Help
---

### Post by garretwp on 2006-11-06
I am having an issue all of the sudden with vmware server. I go to load up the windows xp guest os and for some reason vmware is using 100% of my cpu resources. Windows XP is running really fast and if you go to look at the clock, the seconds are moving fast and not at the normal speed. I have vmware tools installed and also have the time to sync with the host OS. But for some reason I can not get vmware to run normal and not use such a high load. I even tried doing vmware-config.pl to re-compile and still no luck. Does anyone have the same issue as me? Anyway get fix this? I am running edgy with kernel 2.6.17-10-generic.

- Garrett

---

### Post by garretwp on 2006-11-07
Does anyone have any suggestions?

- Garrett

---

### Post by garretwp on 2006-11-08
Well I figured out the problem with the high cpu usage from vmware. I had the memory set for 1024 on vmware and I have a total of 2GB on my system. For some reason, all of the sudden the system did not like vmware using that much ram on the windows xp guest. So I set it to 512 and everything seems to be happy now.

- Garrett

---

