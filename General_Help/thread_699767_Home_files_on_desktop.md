---
title: "Home files on desktop"
date: 2008-02-17
forum: General Help
---

### Post by jeffreyldavidson on 2008-02-17
This may be very simple you someone, but for some reason my files from my home folder just started showingn up on my desktop. I cannot get rid of them because it will delete them from my home folder at the same time. I do not know what cause this to happen.

Please help if you know the solution.

---

### Post by chrisccoulson on 2008-02-17
Press ALT+F2, then run gconf-editor.

In gconf-editor, unset the following gconf key:
```
/apps/nautilus/preferences/desktop_is_home_dir
```

---

