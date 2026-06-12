---
title: "Removing redundant menu items"
date: 2007-04-27
forum: General Help
---

### Post by The Pinny Parlour on 2007-04-27
Hi,

I have many menu items in Applications>Debian>Apps>Net.... that are no longer valid (pointing to a program).  How does one get rid of these?

TIA

---

### Post by rajitsrinivas on 2007-04-27
Its possible that, the .desktop files are still existing in /usr/share/applications folder. Try removing them and see if it helps. Also in /usr/share/app-install/desktop folder. Or do a locate myapp.desktop and delete the files wherever they are.

Disclaimer:If something goes wrong, please replace them from trash :)

---

### Post by The Pinny Parlour on 2007-04-27
> **rajitsrinivas said:**
> Its possible that, the .desktop files are still existing in /usr/share/applications folder. Try removing them and see if it helps. Also in /usr/share/app-install/desktop folder. Or do a locate myapp.desktop and delete the files wherever they are.

Disclaimer:If something goes wrong, please replace them from trash :)

Thanks.  Their in the /usr/share/app-install/desktop     folder but don't have permission to delete them.

---

