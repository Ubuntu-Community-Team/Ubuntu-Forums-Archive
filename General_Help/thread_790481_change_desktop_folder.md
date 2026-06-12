---
title: "change desktop folder"
date: 2008-05-11
forum: General Help
---

### Post by EmilyRose on 2008-05-11
So I upgraded to 8.04 and my "desktop" folder has been set somehow to my home folder - so I now see EVERYTHING thats in it ON My desktop!! How on earth do I change it so that it looks in the folder "Desktop" instead??

---

### Post by nick_h on 2008-05-11
Run
```
gconf-editor
```
and make sure that /apps/nautilus/preferences/desktop_is_home_dir is not checked.

---

### Post by EmilyRose on 2008-05-11
Its not

---

