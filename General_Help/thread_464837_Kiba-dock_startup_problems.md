---
title: "Kiba-dock startup problems"
date: 2007-06-05
forum: General Help
---

### Post by dionysus1983 on 2007-06-05
I've added kiba-dock to the startup programs in system-preferences-sessions, beryl-manager is also added here. But when I log in the desktop-plugin in kiba-dock doesn't show up, and when I exit and restart kiba-dock all is fine. I suspect it's because beryl isn't completely initialized when kiba-dock starts.

So my question is: Is it possible to add a delay in the kiba-dock.desktop file in ~/.config/autostart to make sure beryl is running before kiba-dock tries to start?

---

### Post by maxwellcom on 2007-06-08
Maybe this will work?

[http://ubuntuforums.org/showthread.php?t=396972](http://ubuntuforums.org/showthread.php?t=396972)

---

### Post by dionysus1983 on 2007-06-10
Worked perfectly! Thanks!

---

