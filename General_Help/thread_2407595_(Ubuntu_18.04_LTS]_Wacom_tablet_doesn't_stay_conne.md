---
title: "(Ubuntu 18.04 LTS] Wacom tablet doesn't stay connected"
date: 2018-12-06
forum: General Help
---

### Post by mckempt2 on 2018-12-06
Hello!, I've so far followed a few different guides ([https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) and [https://linuxwacom.github.io/](https://linuxwacom.github.io/)) but while my Wacom Cintiq Pro 13 is connected and can be viewed from the control panel for probably the first 1-2 minutes after reboot, it disappears and I'm no longer able to use my tablet unless I restart (and then I only get 1-2 minutes)

Anyways, I half wonder if it has to do with me being unable to install wacom-dkms (says package is not found), and I also cannot install input-wacom per the other help page because it too cannot find the package in the rep (and I'm 98% sure I added the reps)

Any ideas what I can do next? It works in the sense that my computer sees it at another monitor so I get a picture I just don't get any tablet abilities with it

---

### Post by mckempt2 on 2018-12-09
I tried installing the lastest input-wacom from the release pages, as well as libwacom2, and xf86-input-wacom (from the release pages)

Wondering if this deserves a bug report because I'm out of ideas and Google offers no answers

---

### Post by mckempt2 on 2018-12-18
So it ended up being that the minimal installation of Ubuntu omits wacom drivers. I reinstalled Ubuntu using the Normal option and I now have full functionality

Sucks the Documentation hasn't been updated so I could just add the package to my minimal install. I couldn't find the names of the drivers anywhere to manually install them

---

### Post by eized197 on 2019-03-04
Hi. I'm experiencig the same problem of disconnection after a couple of minutes. If I've well understood, the only thing I have to do is to reinstall Ubuntu 18.04. Thanks a lot for your attention.

---

