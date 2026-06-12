---
title: "Gnome freezes on start up"
date: 2007-12-02
forum: General Help
---

### Post by NBFruit on 2007-12-02
I've been using Ubuntu on my laptop for about a year without any problems.

Now, my Gnome session refuses to start. I login, it loads a few apps and I'm left with the mouse pointer in "please wait" mode. I eventually have to power down at the switch.

I rebooted in Recovery mode, and was able to start a root Gnome session from the command lineusing startx. This works fine. I also have Windows XP installed on the disk, and it works, so I don't think it is a hardware problem.

I've also run fsck on the partition and it doesn't find any errors. Nothing in my .xsession_errors file either. I haven't chnaged anything recently or installed anything new.

I'm stumped. Little help?

---

### Post by NBFruit on 2007-12-02
Problem appears to be with either gnome-power-manager or gnome-update-manager.

I removed both of these as startup programs under Preferences / Sessions in the Gnome session I started as root and on reboot, my own Gnome session started fine. I could see there was a problem with these apps as they both had timer icons next to them under Current Session (ie. they hadn't started correctly).

Don't know whats wrong with them, but at least removing them will get you up and running again.

---

