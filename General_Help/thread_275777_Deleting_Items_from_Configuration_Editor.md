---
title: "Deleting Items from Configuration Editor?"
date: 2006-10-11
forum: General Help
---

### Post by OPaul on 2006-10-11
How do I remove things from the "Configuration Editor"? I have some wireless networks under /system/networking/wireless/networks/ that I would like to remove so NetworkManager will stop automatically connecting to them.

---

### Post by OPaul on 2006-10-13
Anyone?

---

### Post by CatKiller on 2006-10-14
AFAIK, the entries are based on the structure of XML files in your Home directory. Have a look in your Home folder (Ctrl-H to show hidden files) for the .gconf directory. You should have a ~/.gconf/system/networking/wireless/networks/ directory that you can delete or modify.

Good luck.

---

### Post by OPaul on 2006-10-14
Thanks.

---

