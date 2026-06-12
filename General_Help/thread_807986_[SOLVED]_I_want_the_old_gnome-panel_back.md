---
title: "[SOLVED] I want the old gnome-panel back"
date: 2008-05-26
forum: General Help
---

### Post by [censored] on 2008-05-26
Just upgraded from 7.10 - 8.04, using the upgrade-manager. I have my gnome panel set on "Autohide". I find now, after the upgrade, that whenever I move the cursor over the panel, it comes up using a weird slow motion effect, which is not to my taste.

Can anybody tell me either (a) how to stop it doing that, or (b) how to downgrade to an earlier version of gnome-panel? 

Thanks in advance.

---

### Post by Forlong on 2008-05-26
Run
```
gconf-editor
```
Then go to **/apps/panel/toplevels** there look for the entries of your panels -- most probably **top_panel_screen0** and **bottom_panel_screen0** -- and uncheck **enable_animations**

---

### Post by [censored] on 2008-05-27
Thanks Forlong. Is there anyway to disable this animation feature by default?

---

### Post by Forlong on 2008-05-27
Do you mean system wide?

---

