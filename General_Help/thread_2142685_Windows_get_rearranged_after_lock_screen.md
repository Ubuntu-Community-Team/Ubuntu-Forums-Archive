---
title: "Windows get rearranged after lock screen"
date: 2013-05-06
forum: General Help
---

### Post by sulobanks on 2013-05-06
Hello

I've had a problem with window placement for several versions of Ubuntu.  I have a Mac Pro tower with a Radeon HD 5770 installed.  I have 2 1920x1080 monitors connected.  Dual screen works fine using either the open source or the proprietary drivers.  The problem I have is that when I lock the screen or the monitors fall asleep, I log back in to find my windows rearranged and moved to different desktops.  I tried switching to KDE and the problem went away, and this would be an acceptable solution if not for the fact that I just don't like KDE.  Has anyone else seen this problem?  If so, were you able to fix it?  I have the same problem on another machine.  AMD quad core Phenom II with Radeon HD 5450, so it's not limited to just the one machine.

Thanks

---

### Post by sulobanks on 2013-05-08
Just to update, the success on KDE was short lived.  Same problem.  It seems the system insists on moving things to one screen when it detects only one screen connected, even if that's only for a second or two.  Has anyone else seen this, or better yet, fixed it?

---

### Post by sulobanks on 2013-05-10
Just in case someone else has the same problem and reads this, I'll post what I've done to fix it.  One of the problems is DPMS.  The monitors power off after awhile and the system detects no monitors plugged in.  This computer is sitting at my desk at the office, so there's no reason to worry about power management.  I can just turn the monitors off manually before I leave for the day.  So I lock the screen, then switch off the power management on both monitors.  When I come in the next morning, I turn on the monitors and unlock the screen and everything is right where I left it.  It's been working that way for a couple of days now.

Clearly, I haven't managed to figure out what mechanism should be remembering where the windows last were when the screens fell asleep, and thus, haven't fixed that.  However, this workaround works for me at present.

---

