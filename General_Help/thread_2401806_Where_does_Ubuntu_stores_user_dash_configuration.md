---
title: "Where does Ubuntu stores user dash configuration?"
date: 2018-09-22
forum: General Help
---

### Post by fa3d on 2018-09-22
Hello. Quick question. Where does Ubuntu stores user dash configuration (favorite applications pinned in the dash and their position, etc.)?

---

### Post by deadflowr on 2018-09-22
dconf/gsettings
Install dconf editor and look in org.gnome.shell, there is where you should see dash entries added to favorite-apps item.
(Also look ibn the sub section extensions and the dash-to-dash section within that as well)
All dconf user settings are stored in a binary file in ~/.config/dconf/user.

---

