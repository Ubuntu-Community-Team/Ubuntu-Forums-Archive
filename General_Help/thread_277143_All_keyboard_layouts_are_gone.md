---
title: "All keyboard layouts are gone"
date: 2006-10-14
forum: General Help
---

### Post by wireless on 2006-10-14
Hi ALL

suddenly i have no language indicator and when checked in "regitional and accessibilty"-> "keyboard layout" its empty and when i check "enable kyboard layout" and apply it un apply itself. and the "keyboard model" is empty. 
i have no idea what i done to make those changes , any hit will be gr8!

thnx in advanced

---

### Post by wireless on 2006-10-15
HELLO
need help SOS .

---

### Post by wireless on 2006-10-16
OK FOUND THE ANSWER AND FIXED IT
1: delete /usr/share/X11/xkb
2:create symlink sudo ln -s /etc/X11/xkb /usr/share/X11
and thats it :):cool:

---

