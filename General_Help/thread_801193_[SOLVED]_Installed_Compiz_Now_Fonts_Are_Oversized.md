---
title: "[SOLVED] Installed Compiz Now Fonts Are Oversized"
date: 2008-05-20
forum: General Help
---

### Post by ChompTheMan on 2008-05-20
I am using Kubuntu 8.04 with KDE 3.5.  I installed Compiz yesterday and everything went fine.  When I turned on my computer today and logged in I found that most of my fonts are now oversized.  I checked the settings in Kcontrol and nothing has changed there.  I have the following installed:

```
compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins libcompizconfig0 compiz-kde compiz-plugins compizconfig-backend-kconfig compizconfig-settings-manager kicker-compiz kicker-taskbar-compiz xserver-xgl fusion-icon
```

Anyone know how to fix this?  Setting my window manager back to kwin does not fix the problem.

---

### Post by ChompTheMan on 2008-05-20
Well, I just solved my problem.  I removed 'xserver-xgl', restarted X, and everything is back to normal.

---

