---
title: "Can't log in to Unity 3D"
date: 2012-11-03
forum: General Help
---

### Post by NautiusMaximus on 2012-11-03
I have recently been unable to login to Ubuntu in Unity 3D mode. I can log into Unity 2D mode without problems.

When the problem first started, I checked the log files, and found this in my syslog file around the time I tried to log in:

```
Oct 28 17:09:14 beast kernel: [  202.447509] show_signal_msg: 39 callbacks suppressed
Oct 28 17:09:14 beast kernel: [  202.447512] compiz[1939]: segfault at 0 ip           (null) sp 00007fff049bbe88 error 14 in compiz[400000+c000]
Oct 28 17:09:23 beast gnome-session[1873]: WARNING: Application 'compiz.desktop' killed by signal
Oct 28 17:09:23 beast gnome-session[1873]: WARNING: App 'compiz.desktop' respawning too quickly
Oct 28 17:09:23 beast gnome-session[1873]: CRITICAL: We failed, but the fail whale is dead. Sorry....
```

A little bit of googling suggested I could try fixing the problem by typing 

```
unity --reset
```

I tried this, but I still can't log in. However, the error messages about compiz are now gone from my syslog file. In fact I can't find anything in my syslog file that looks like it's reporting an error at the time I try to log in.

Unity 2D still works just fine.

I'm using Ubuntu 12.04 with NVidia proprietary drivers.

Any ideas what to check next?

Thanks
NM

---

### Post by grahammechanical on 2012-11-03
Could you please explain what happens when you try to log in to Ubuntu 3D? Do you not get an option for Ubuntu at the login screen? Do you only see Ubuntu 2D?

Or does a problem occur after you select Ubuntu and then log in?

When in 2D mode you could try using the Ubuntu Software Centre to remove Compiz openGl window and compositing manager and install it again.

Compiz is not used when in 2D mode so removing it will not break the desktop but Compiz is necessary for 3D mode and re-installing it might, just might fix this problem.

Regards.

---

### Post by NautiusMaximus on 2012-11-03
Thanks for the reply. Yes, I was a bit light on the detail of the manner in which it didn't work, wasn't I?

OK, so what happens is this. When the logon screen appears (either after logging out or after a reboot), I have the choice of logging on to either Ubuntu or Ubuntu 2D. If I choose Ubuntu 2D, everything is fine.

If I choose Ubuntu, then it seems to accept my password, but it presents me with a completely non-functional desktop consisting of my normal background picture and a cursor, nothing else. I can move the cursor around with the mouse, and I can call up a command line interface by pressing Ctrl-Alt-F1, but that seems to be all I can do.

I looked at uninstalling compiz as you suggested. It says that it needs to remove Unity before it can do that, which seems like a rather drastic step, doesn't it?

Thanks
NM

---

