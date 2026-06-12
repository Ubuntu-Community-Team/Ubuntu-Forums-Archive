---
title: "Libreoffice &quot;main panel missing&quot; laucher. ubuntu 18.04"
date: 2018-06-23
forum: General Help
---

### Post by ubname on 2018-06-23
Is it possible to enable the libreoffice "main panel" ( do not know the exact name)
the one that it is launched using the white icon, the white icon is missing in ubuntu 18.04.
I find it very useful because i can look at the document i'm working on being it a spreadsheet or a presentation.
is there some way to restore that white icon in ubuntu 18.04?

Thanks

---

### Post by vanadium on 2018-06-23
It is there, but it has the instruction "NotShowIn=GNOME;". I see it in my Albert Launcher, but not in Gnome Shell indeed.

A safe solution (no root intervention needed): copy the /usr/share/applications/libreoffice-startcenter.desktop file to your .local/share/applications folder. Comment out the line NotShowIn=GNOME; (place a # in front of the line). Should now appear in your gnome launcher.

---

### Post by ubname on 2018-06-25
I would like to thank you and your solution works.

---

