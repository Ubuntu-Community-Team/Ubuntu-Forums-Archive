---
title: "Wine menu problem"
date: 2007-11-18
forum: General Help
---

### Post by icechen1 on 2007-11-18
HI

I installed some windows programs using wine,they appeared in the Applications->Wine->Program menu but since i installed wine doors,they disappeared and i tried reinstalling wine and removing wine-doors,no luck.Although i can see the folder containing them in menu editor(alacarte) but there is no file(or shortcut) inside.Is this a bug?

Any help is appreciated. ;)

---

### Post by pyro_xp2k on 2007-11-19
In Wine-Doors, go to Edit > Preferences, and select "Show Wine Programs Menu."

---

### Post by icechen1 on 2007-11-25
> **pyro_xp2k said:**
> In Wine-Doors, go to Edit > Preferences, and select "Show Wine Programs Menu."

 :( nothing happened when i did that...

---

### Post by icechen1 on 2007-11-25
Fixed!I did as root,set the permission of the directories in /home folder/.local/share back to my user(it was root before) then problem fixed.reinstall the apps and they reappear in the menu. :)l

---

