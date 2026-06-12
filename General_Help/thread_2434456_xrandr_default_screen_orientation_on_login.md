---
title: "xrandr: default screen orientation on login"
date: 2020-01-06
forum: General Help
---

### Post by Tapani_Simojoki on 2020-01-06
Having once shut down my machine (Ubuntu 19.04) with the screen in portrait orientation, the following now occurs every time:

Up to the Ubuntu login screen, the screen is in landscape mode. When I log in, I find the screen in portrait mode, and I have to switch to landscape.

Despite numerous searches, and probably owing to incompetence, I haven't found a way to change the default login orientation back to landscape.

UPDATE: This is true of every desktop environment on my system (Gnome, Gnome Flashback [Metacity], Ubuntu) except Unity.

---

### Post by CatKiller on 2020-01-06
As a potentially sledgehammer approach, the monitor settings for after you've logged in are stored in ~/.config/monitors.xml. You could try editing / renaming that. I don't know if Gnome stores additional versions of its settings elsewhere.

---

### Post by Tapani_Simojoki on 2020-01-06
Yes, that works.
However, what I don't understand is why that would have not been updated every time.

---

