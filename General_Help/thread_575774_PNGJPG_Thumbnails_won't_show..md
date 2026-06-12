---
title: "PNG/JPG Thumbnails won't show."
date: 2007-10-14
forum: General Help
---

### Post by patchoro on 2007-10-14
Woops, wrong header : JPG pose no problems 

Suddenly my PNG files are no longer thumbailed. 
Other files are thumbnailed just fine. (jpg/avi/mpg/pdf/cbr etc etc)

Since other files are thumbnailing allright I guess it isn't a thumb-configuration issue.
Did I somehow kill a essential dependency / application?

I use Ubuntu 7.04 with Gnome.

---

### Post by patchoro on 2007-10-15
Found a solution:

To resolve I removed the ~/.local/share/mime folder. This folder is a cache of mime infos, removing it nautilus will use system configuration instead of local one.

---

### Post by wanchai on 2008-03-08
Yeah! Thanks.

My problem was with gthumb completely ignoring png and jpg. Likewise, the dialog to change the desktop background wouldn't show jpg and png when the "Images" filter was on. Deleting this mime folder solved the problem.

---

