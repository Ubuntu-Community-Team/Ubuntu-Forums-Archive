---
title: "[SOLVED] 14.10 + KDE Next + SDDM; can not switch to console"
date: 2014-11-11
forum: General Help
---

### Post by cyberwizzard2 on 2014-11-11
I just upgraded from 14.04, removed the old neon KDE5 packages, rebooted, added KDE Next PPA, upgraded all packages to get the plasma-desktop environment. Then I installed SDDM and the KDE configuration module for that.
It's working fine, I can log in, log out, use the KDE5 desktop.

At that point I notice that I can not switch to the console from within the X session: pressing Alt+Ctrl+F1 (up to F6) does not bring me to the console. Not when SDDM is active or when I already logged in.

Is this intended behaviour? And if so, how do I enable switching to consoles again (like it was possible in every *buntu in the past).

Edit: solved!

Kubuntu 14.10 supports multiple consoles just fine. At some point I suspected systemd but it turns out that consoles are spawned when you switch to them; e.g. they do not exist before that point.

In the end it I found out that both SDDM and LightDM started. As SDDM was first, that one showed up and the start of LightDM caused some weird conflict (including some flashes to a black screen within SDDM) where keystrokes in the window manager were not processed properly. I removed LightDM completely, rebooted and suddenly the VT switching works again as intended.

---

