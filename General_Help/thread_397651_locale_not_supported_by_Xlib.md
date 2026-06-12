---
title: "locale not supported by Xlib"
date: 2007-03-30
forum: General Help
---

### Post by Lucifiel on 2007-03-30
Hey, I am trying to setup ntfs-3g right now. However, whenever I paste the command below into Terminal:
gksu gedit /etc/apt/sources.list, I get these errors:


(gksu:9132): Gdk-WARNING **: locale not supported by Xlib

(gksu:9132): Gdk-WARNING **: cannot set locale modifiers

(gedit:9133): Gdk-WARNING **: locale not supported by Xlib

(gedit:9133): Gdk-WARNING **: cannot set locale modifiers

(gedit:9133): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I've already switched the language back to English(United States of America). Previously, it was set as English(Singapore).

Is there anything else I can do to resolve this issue? =/

---

### Post by zvacet on 2007-03-31
```
gksudo gedit /etc/apt/ sources.list
```

If you still have problems try to install xlib with synaptic.

---

### Post by Lucifiel on 2007-03-31
Thank you. It turned out that my installation of Ubuntu was messed up. So, I'll see if this installation still has the same problems. :)

---

