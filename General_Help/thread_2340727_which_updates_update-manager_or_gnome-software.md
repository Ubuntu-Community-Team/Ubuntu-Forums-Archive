---
title: "which updates? update-manager or gnome-software"
date: 2016-10-21
forum: General Help
---

### Post by jaarvidsen on 2016-10-21
which updates am i supposed to use? cos gnome-software displays waaay more updates than update-manager

---

### Post by deadflowr on 2016-10-21
Use which ever one you prefer, or even ignore both and use the traditional command line utilities to update.

The issue of why gnome-software has more updates, than update manager(software updater) is typically because update-manager has something called phased-updates builtin, where as gnome software doesn't.

In a nutshell, phased-updates is a process in which the update team releases updates incrementally. First to a small set of users, and then if no errors they increase it till eventually all users get the updates.
If errors start hitting a set threshold, then the updates get pulled. So only a relative small user base get affected, rather than the whole user base.

See [https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")
for added reference.

---

### Post by jaarvidsen on 2016-10-21
thanks for the quick reply and excellent explanation!

---

