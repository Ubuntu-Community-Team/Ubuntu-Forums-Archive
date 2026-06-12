---
title: "Pidgin no longer starts automatically in Gutsy"
date: 2008-01-16
forum: General Help
---

### Post by wheezer on 2008-01-16
Pidgin used to start up automatically in Feisty.  But in Gutsy, it just doesn't.  I have "use status from last exit at startup, but it doesn't do it.

I am tempted to reinstall, but afraid of losing my configs.  How can I back those up? Where are the pidgin configurations stored?

---

### Post by linuxwizard on 2008-01-16
Compiz and session management

Users who enable desktop effects will find that they are unable to use the "Remember currently running applications" feature. The workaround for this issue is to disable the use of the Compiz compositing window manager by turning off desktop effects in the System -> Preferences -> Appearance menu.

[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

---

### Post by ThrobbingBrain66 on 2008-01-16
> **wheezer said:**
> Pidgin used to start up automatically in Feisty.  But in Gutsy, it just doesn't.  I have "use status from last exit at startup, but it doesn't do it.

I am tempted to reinstall, but afraid of losing my configs.  How can I back those up? Where are the pidgin configurations stored?

If, when you say 'use status from last exit at startup' you're talking about that option within the Pidgin preferences, it won't work.  That only deals with your away/busy/available status.

Check to make sure that Pidgin is still set to start at startup:

Go to System > Preferences > Sessions and make sure that Pidgin is in the startup program list and that it's box is ticked.

---

### Post by wheezer on 2008-01-16
That's what I was looking for.  Thank you.  I never say the startup list.   I guess Pidgin used to insert itself there in early version, and doesn't now.

Time to reboot and try it.

---

### Post by wheezer on 2008-01-16
NOPE. 

I enter 'pidgin with command pidgin in startup sessions.  It's checked and ok.

But when I reopen preferences > sessions again, it's gone.  Naturally, it's not there at startup either.

What to do?

---

### Post by linuxwizard on 2008-01-16
Try this than

[https://answers.launchpad.net/ubuntu/+question/12430](https://answers.launchpad.net/ubuntu/+question/12430)

---

### Post by wheezer on 2008-01-16
Solved.

For some reason, the 3rd time I tried, I "edited" and did nothing., but it make the Pidgin entry stick!

THanks!

---

