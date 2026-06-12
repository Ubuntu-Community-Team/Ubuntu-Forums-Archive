---
title: "Remove Desktop Hard Drive Icons"
date: 2008-03-24
forum: General Help
---

### Post by quddusaliquddus on 2008-03-24
Hi all :)
       I want to remove the icons of my hard drives that are on the ubuntu desktop. I know this has been covered before but I dont know what 'mounting' is as I am not versed in such things.

Could someone help please?

Many thanks

Regards :D

Q

---

### Post by y-lee on 2008-03-24
If I understand what you want corectly you need to open the gnome configuration editor

```
gconf-editor
```


and go to **apps/nautilus/desktop/** and uncheck the** volumes_visible** checkbox and maybe the **computer_icon_visible** if you wish :)

---

### Post by quddusaliquddus on 2008-03-24
Thanks for the reply.

I cant seem to find the gnome configuration editor in the menus.

---

### Post by quddusaliquddus on 2008-03-24
its ok. i found it. thanks again

---

