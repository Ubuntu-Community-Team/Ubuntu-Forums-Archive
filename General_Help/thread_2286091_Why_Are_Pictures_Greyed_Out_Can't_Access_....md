---
title: "Why Are Pictures Greyed Out? Can't Access ..."
date: 2015-07-09
forum: General Help
---

### Post by Rick St. George on 2015-07-09
Used Sudo Thunar to copy a picture to usr/share/xfce/backdrops  for use as background image.  It doesn't show up in Desktop / Properties / Backgrounds.
Upon going to file Manager and browsing to the folder, the picture has a LOCK on it and permissions are set to Root.

Browsed to Pictures and they are all like that.  What happened ???  How can I change the permissions?

Thanks,
Rick

---

### Post by kerry_s on 2015-07-09
there suppose to go in /usr/share/backgrounds for system wide & ~/.local/share/backgrounds or you can just put them in any folder & use the add button. i think by default it checks your pictures folder.

really you can just right click any image-> set as background no matter where it is.

you can go back in as root & right click-> properties to change the permissions.

---

### Post by Rick St. George on 2015-07-10
Went back in as Root, modified pic Permissions (added Me), then it showed up in Desktop / Properties / Backdrops in Xubuntu v14.04 LTS.

Who would've thought that was needed.
Case Closed.

Thanks!
Rick

---

### Post by oldos2er on 2015-07-10
> **Rick St. George said:**
>   What happened ??? 

You used "sudo" so root ownership of the picture was preserved. Open two thunar windows normally (i.e. without sudo) and drag and drop picture files from /usr/share/xfce4/backdrops to the Pictures folder of your home user. No "sudo" needed, and no unnecessary permission or ownership changing needed either.

---

