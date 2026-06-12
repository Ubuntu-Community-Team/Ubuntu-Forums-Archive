---
title: "Logout on laptop lid close"
date: 2016-02-28
forum: General Help
---

### Post by Medeo on 2016-02-28
Currently on Xubuntu 14.04.4. When I close my laptop, I want it to do nothing except blank the screen. By default, it suspends.

So I went to Settings > Power Manager and selected "Nothing" on "When laptop lid is closed:" for both AC and Battery, then rebooted. For whatever reason, it decided to ignore this and suspends anyway. 

So then I went into /etc/systemd/logind.conf, uncommented HandleLidSwitch, set it to "ignore", then restarted systemd-logind. Now it no longer suspends, but it does log me out of my session. When I open the lid again, I'm back at the login splash screen and all my running programs are gone. Frustrating.

Now, I've been able to "solve" the problem by killing xfsettingsd, so I can assume that it's XFCE that's at fault here, but obviously that's a less-than-desirable workaround. Any ideas what might be causing this? :confused:

---

### Post by dave157 on 2016-02-28
There should be an apply in the right bottom corner of the power configuration screen once changing settings. 

/etc/systemd/logind.conf, uncommented HandleLidSwitch, set it to "ignore"

Or some have used

/etc/systemd/logind.conf, uncommented HandleLidSwitch, set it to "ignore true" 

if you did click apply and it did not take try the above.

---

### Post by dave157 on 2016-02-29
Though I would have the screen go off when it is closed that will help your battery last longer.

---

