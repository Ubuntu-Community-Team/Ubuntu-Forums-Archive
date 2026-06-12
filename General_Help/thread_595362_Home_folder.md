---
title: "Home folder"
date: 2007-10-28
forum: General Help
---

### Post by DagonX on 2007-10-28
I did a fresh insal Gutsy X64. Now it won't let me drag the "home" folder to the desktop. Is there any way to move the home folder to the desktop?

---

### Post by Clay_Banger on 2007-10-28
the reason that you can not copy the home folder to the desktop, is that 'desktop' is a sub folder of the home dir. what you need to do is create a shortcut to the home folder and place it on the desktop. as i am a kde user, i have no idea how that is done, but im sure google will be able to help you now that you know what your looking for.

---

### Post by nick_h on 2007-10-28
Type:
```
gconf-editor
```
Under apps/nautilus/desktop set home_icon_visible

---

### Post by DagonX on 2007-10-28
Thanks, that works

---

