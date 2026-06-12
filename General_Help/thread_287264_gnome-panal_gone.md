---
title: "gnome-panal gone"
date: 2006-10-28
forum: General Help
---

### Post by Ocxic on 2006-10-28
after installing a new mouse theme I accentedaly hit apply new theme in the theme browser and now my panels are gone:
i get this error whe i run gnome-panel from the cli:

```

(gnome-panel:6759): Gtk-WARNING **: Theme file for neutral has no directories


(bug-buddy:6764): Gtk-WARNING **: Theme file for neutral has no directories

```

i figure that i need to change my theme, is there anyway to do that from the cli???

Solution:

remove neutral theme folder from /home/ikrel/.icons/"neutral" <---rmoved folder

the folder name may change depending on the theme installed.

---

