---
title: "Saving gconf settings"
date: 2007-02-26
forum: General Help
---

### Post by CocoAUS on 2007-02-26
Is there any way I can save/export my gconf settings for rebuilding/deployment purposes?  I imagine I could write a script to set up the values properly, but it seems to me there must be an easier way.

---

### Post by louis_nichols on 2007-02-26
Sure. You can just save the folder ~/.gconf . This is where they're all saved. Please note that most of times, for a given application, not all settings will be in gconf.

---

