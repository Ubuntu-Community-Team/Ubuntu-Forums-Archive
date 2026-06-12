---
title: "Can't run xubuntu session (works on guest)"
date: 2012-11-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-11-07
i purged all nvidia drivers, and removed the boot resolution fix
put my hdd in a intel system
every time i login to my account using a xfce session or xubuntu session the screen goes blank for a second then i hear gmusicbrowser playing, i can use my keyboard controls for it, but my desktop does not display
guest session works as expected
what file do i need to delete
i tried .Xautiority and .ICEauthoriy

---

### Post by pqwoerituytrueiwoq on 2012-11-07
Solution:
```
rm ~.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
```
i found other things than can cause this, like bad permissions on /etc/xdg/autostart/*

---

