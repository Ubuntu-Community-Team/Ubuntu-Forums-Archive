---
title: "Adding complicated Menu Items"
date: 2013-01-18
forum: General Help
---

### Post by alphaamanitin on 2013-01-18
I want to open LibreOffice and Zotero at the same time as LibreOffice has to have Zotero running in firefox or stand alone to use the LibreOffice plugin.  I already have made a new menu item to open Zotero, but how do I make a new menu to open them both at once?

I thought the commad should be thus > libreoffice --writer %U && ~/Zotero/run-zotero.sh or > libreoffice --writer %U; ~/Zotero/run-zotero.sh

Any thoughts?

Should I just make a command line alias?

AlphaA

---

### Post by LewisTM on 2013-01-18
You're going to run into two problems if you use these commands in an Xfce launcher

1) Xfce doesn't interpret shell syntax like **~**, **;** and **&&**. So only the first command will run. You need to wrap the whole thing inside a call to a shell.

2) Even if you managed to make the chained commands work, it would wait for LibreOffice to quit before executing Zotero. You want to run both in parallel right? For that, you need to fork Libreoffice with a single &.

So the command to put in your launcher would be:
```
bash -c "libreoffice --writer %U & ~/Zotero/run-zotero.sh"
```

Cheers!

---

### Post by alphaamanitin on 2013-01-21
Thanks, that worked.  Just finally got around testing it.

AlphaA

---

