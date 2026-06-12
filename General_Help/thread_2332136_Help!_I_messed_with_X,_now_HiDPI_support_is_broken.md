---
title: "Help! I messed with X, now HiDPI support is broken in browsers!"
date: 2016-07-28
forum: General Help
---

### Post by Zorgoth on 2016-07-28
I was playing around with trying to start X sessions and at some point made the mistake of attempting a start an X session as root from my home directory, which prevented me from logging into a desktop session. I deleted a few config files to see what was wrong before figuring out that the problem was .XAuthority. After I got my desktop back, HiDPI support was broken in both Chrome and Firefox. I can workaround chrome by starting it with the --force-device-scale-factor flag, but I'd rather not. I sometimes change my resolution for games, so I'd need multiple launchers with different scale factors.

---

### Post by Zorgoth on 2016-08-03
Somehow some settings got messed up (I didn't delete those files, so G-d knows how). I fixed it by running

gsettings set com.canonical.Unity.Interface text-scale-factor 1.0
gsettings set org.gnome.desktop.interface text-scaling-factor 1.5

---

### Post by Zorgoth on 2016-08-03
Never mind, not really fixed. Now everything in the dash is off-center and ugly.

---

### Post by Zorgoth on 2016-08-03
Never mind, fixed after all. Relogged and ran

gsettings reset com.canonical.Unity.Interface app-scale-factor-monitor

because I accidentally unset and set it and wondered if I had made a typo. Then everything was fine.

---

