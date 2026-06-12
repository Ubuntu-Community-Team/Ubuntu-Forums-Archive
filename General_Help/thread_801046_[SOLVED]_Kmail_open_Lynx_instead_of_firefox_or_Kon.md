---
title: "[SOLVED] Kmail open Lynx instead of firefox or Konqueror"
date: 2008-05-20
forum: General Help
---

### Post by rbmorse on 2008-05-20
Running 8.04 with both GNOME and KDE4 desktops installed. I generally prefer GNOME, but like Kmail/Kontact better than Evolution. The only issue is that in either environment if I click on an embedded link in a message in kmail I get shell window running lynx instead of one of the expected GUI browsers (prefer Firefox, but I'll take Konqueror). 

I have tried to set file types in Konqueror's settings in both desktops, but I still get Lynx. Would appreciate any suggestions.

---

### Post by rbmorse on 2008-05-20
Found the majicks. 

From a user terminal, kcontrol > KDE Components > File Associations. Enter html into the dialog box and change the default app setting in BOTH categories (html, txt) that appear.

---

