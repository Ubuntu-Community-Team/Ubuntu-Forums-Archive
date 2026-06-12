---
title: "Antialiasing in GNOME apps under KDE disappeared after upgrade"
date: 2006-10-28
forum: General Help
---

### Post by Foucault on 2006-10-28
Hello everyone,
I've just upgraded via update-manager from Dapper to Edgy. Everything seems to have gone fine however I have slight problem with the fonts of GNOME applications under KDE (I am using KDE as my default desktop). Any gnome application started under KDE has no antialiasing for its fonts. Is there any way to fix that? I've changed the settings under gnome-font-properties which seems to fix the problem, however after re-login antialiasing is lost again. I've also tried the KControl Module for GTK applications but no luck.

Any ideas?
Thank you in advance.

---

### Post by Foucault on 2006-10-29
Well, for anyone that might be interested I've fixed that by inserting the line:

```
gnome-settings-daemon &
```

at line ~315 of the /usr/bin/startkde script (which apparently loads KDE)

---

