---
title: "Printing in wine?"
date: 2007-02-12
forum: General Help
---

### Post by an.echte.trilingue on 2007-02-12
Hey all.

I can't print when running MS Office 2003 in wine.  In the printer dialogue, I can "see" and select my printer, but the "status" line says that the printer is inactive and printing, of course, does not work.

Anybody know how to get printers working in wine?

Thanks
-mat

---

### Post by barney_1 on 2007-02-12
I would try two things.

First, make sure that your printer is the default printer in Ubuntu's printer settings.

Second, restart cups:
```
sudo /etc/init.d/cupsys restart
```

Hope this helps!

---

### Post by an.echte.trilingue on 2007-02-14
Still nothing.

Thank you, though.

Take care
-mat

---

