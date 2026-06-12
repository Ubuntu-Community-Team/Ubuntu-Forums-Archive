---
title: "Xubuntu 14.04 saves session even though configured not to"
date: 2014-04-22
forum: General Help
---

### Post by cbraxton on 2014-04-22
A minor annoyance, but an annoyance nonetheless -- when shutting down my Xubuntu 14.04 system, if anything was left running at shutdown time it is automatically started up again on the next boot. This occurs even though the "Session and Startup" settings page does NOT have the "Automatically save session" check box enabled. Is there somewhere else this needs to be disabled? (I normally use the "Action Buttons" panel applet to shut down if that makes a difference.)

---

### Post by bkline on 2014-04-22
I have a similar problem (pre-dating 14.04), except that an app doesn't actually need to have been running at the end of the previous session to pop up at the beginning of the next session. This is using xcfe.

---

### Post by Jordan_Cameron on 2014-04-22
Out of curiousity have you tried deleting your ~/.config/xfce folder and rebooting.  If you do so, first thing I would do is uncheck the "Automatically save session" box again.  You will have to reconfigure your setup/theme but first thing to try imo is to restore xfce to default.

---

### Post by cbraxton on 2014-04-23
> **Jordan_Cameron said:**
> Out of curiousity have you tried deleting your ~/.config/xfce folder and rebooting.  If you do so, first thing I would do is uncheck the "Automatically save session" box again.  You will have to reconfigure your setup/theme but first thing to try imo is to restore xfce to default.

I gave that a try and it did fix the problem, so something must have gotten corrupted in the xfce settings. Fortunately being a new installation there are not a lot of customizations to reconfigure.

---

