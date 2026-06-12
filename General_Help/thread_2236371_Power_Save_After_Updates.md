---
title: "Power Save After Updates"
date: 2014-07-26
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2014-07-26
I'm currently on Xubuntu 14.04, 64 bit.  Auto login, all power save features switched off, screensaver switched off.
This morning (26th July) got the standard pop up to advise of updates, so went ahead.
Since then, ag=fter around 10 minutes of not being used, the screen blanks, as if power saving or screen saver were kicking in.
I've checked the poewr and screen save settings, they haven't changed.
Anyone know why this has suddenly started to happen?
I realise that I could install caffeine or similar, but would rather find why this has started after updates.

Thanks in advance

---

### Post by Dennis N on 2014-07-26
With the 10 min time you give, sounds like the Display Power Management System (DPMS) at work.

This solution worked for me, written for Lubuntu, but applicable to Xubuntu - install xscreensaver and use Xubuntu's startup applications dialog to be sure it autostarts. Also I uninstalled light locker and set power manager to never put the monitor to sleep. 

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15)

It works because Xscreensaver overrides DPMS. From Arch Wiki:
> XScreenSaver manages display energy saving (DPMS) independently of X itself and overrides it. To configure the timings for standby, display poweroff and such, use xscreensaver-demo or edit the configuration file manually, e.g. ~/.xscreensaver

source: [https://wiki.archlinux.org/index.php/XScreenSaver](https://wiki.archlinux.org/index.php/XScreenSaver)
:

---

### Post by Y^2om&amp;#7sgP on 2014-07-27
Thanks for that Dennis N.  Removed light locker re-installed xscreensaver and back to normal.
I hadn't found the bug report when searching before.  Interesting that it's just kicked in, but glad it's working again.

---

