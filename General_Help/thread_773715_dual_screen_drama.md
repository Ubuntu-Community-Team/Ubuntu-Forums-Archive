---
title: "dual screen drama"
date: 2008-04-29
forum: General Help
---

### Post by jhyland87 on 2008-04-29
hey, so I have 2 22" monitors, and I have an asus EN8600gt graphics card.


I tried a tutorial that showed me how to set it up with a gforce graphics card, and my computer would no longer start up in GUI mode, that took a long time to fix...

anyone else have DS with this card? how did you set it up.

---

### Post by jhyland87 on 2008-04-29
> **jhyland87 said:**
> hey, so I have 2 22" monitors, and I have an asus EN8600gt graphics card.


I tried a tutorial that showed me how to set it up with a gforce graphics card, and my computer would no longer start up in GUI mode, that took a long time to fix...

anyone else have DS with this card? how did you set it up.

bump :confused:

---

### Post by ryanhaigh on 2008-04-29
Once you install the drivers using restricted driver manager (system>admin>restricted driver manager) restart the computer (or just X if you know how), login press alt-f2 to bring up the run application dialog and enter nvidia-settings. You should be able to configure things the way you want using that. If you can get them the way you want run the application again using gksudo nvidia-settings so that you are running as admin/root, make your changes and save the configuration to xorg.conf (theres a button for this)

This is how I got my 8600GT Configured.

---

