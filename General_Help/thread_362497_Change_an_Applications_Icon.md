---
title: "Change an Applications Icon"
date: 2007-02-15
forum: General Help
---

### Post by Noah0504 on 2007-02-15
I found a replacement icon for MPlayer and I would like to know how to change the default icon with mine.

---

### Post by crossedout on 2007-02-15
Are you using a default theme or one that you installed yourself?

If using one of your own (ie from gnome-look.org, etc) then just copy that icon to the appropriate folder.
Open home folder, ctrl+h (to show hidden files/folders).  Navigate to .icons/CURRENTTHEMENAME/APPS and paste the icon in there.

If using a default theme and don't want to install your own, you'll have to use sudo to rename the mplayer icon to ICONNAME-OLD (assuming you don't want to overwrite it) and copy the new one to the current theme's directory.

-Xout

---

