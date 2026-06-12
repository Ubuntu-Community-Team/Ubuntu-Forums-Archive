---
title: "Alt F10 not working (unity and keyboard settings use same key)"
date: 2013-04-22
forum: General Help
---

### Post by trafo23 on 2013-04-22
Hi,
Alt F10 is no longer working in 12.04 to toggle between maximized and normal window. I can see that Unity is using the same key. The problem is that even if i disable the "Key to open the first panel menu" option in ccsm it still wonät work. 

Obviously i don't want what Unity is offering me for the alt F10.

Is there a way to fix this?

Regards

---

### Post by dino99 on 2013-04-22
use dconf-tools or unity-tweak-tool to set your preferences

---

### Post by trafo23 on 2013-04-22
Thanks, i will check them out. But what is the point of CompizConfig if it does not work?

Regards.

Edit: Tried the suggested workaround:

dconf write /org/gnome/desktop/wm/keybindings/toggle-maximized "['<Super>Return', '<Alt>F10']"

But it still does not work. Perhaps unity overrides it somewhere?

---

### Post by trafo23 on 2013-06-18
Please advise, it still does not work!

I can think of three ways to change the keyboard bindings:
1) ccsm
2) gconf-editor
3) system settings

Which is the correct place? How is it possible that all of these programs display different settings?  What a mess !

LONG LIVE WINDOWS!!!!!!!

---

