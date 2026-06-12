---
title: "How to adjust low battery shutdown level?"
date: 2008-04-26
forum: General Help
---

### Post by MikeyXX on 2008-04-26
I get a warning that my battery is low, but I want it to auto-shutdown at 5% or something like that. Right now it suddenly crashes due to low battery. Windows as the ability to adjust when I want it to shutdown gracefully, where is it in linux, anyone know?

---

### Post by sdennie on 2008-04-26
You should be able to adjust that setting via System->Preferences->Power Management.  However, if you would really like to fine tune those settings, you may want to use gconf-editor and go to /apps/gnome-power-manager.  There are a lot of hidden settings that aren't available to adjust via a GUI.

---

### Post by MikeyXX on 2008-04-29
That did it. The gconf-editor, not the power manager. Thanks.

---

