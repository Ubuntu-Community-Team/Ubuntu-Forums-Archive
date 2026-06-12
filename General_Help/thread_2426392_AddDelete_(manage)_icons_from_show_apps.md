---
title: "Add/Delete (manage) icons from show apps"
date: 2019-09-08
forum: General Help
---

### Post by mrbean04 on 2019-09-08
Hi everyone! :)
I recently installed some Windows applications with Wine.
All works fine, but the only problem is that some applications have uninstall files (such as "uninst000.exe" or "uninstall.exe"), and those applications show up in my "show apps" list.
I searched for any solution about that, and I couldn't find anything.

So, anyone knows how to manage those icons from "show apps" ?

Thanks. :)
(P.S. I use Ubuntu 18.04.3 LTS)

---

### Post by Holger_Gehrke on 2019-09-08
If it behaves like Wine on my XUbuntu 18.04, then it creates .desktop-files in ~/.local/share/applications/wine/Programs when a Windows setup program makes the calls to create a menu-item in Windows. Deleting or moving them outside ~/.local/share/applications should remove them. Alternatively you could open the ones you don't want in an editor and add a line saying 'Hidden=yes' or 'NotShowIn=Gnome'.

Holger

---

### Post by mrbean04 on 2019-09-09
Thanks for the reply. Actually the 1st method works fine for me. Deleting the *.desktop files worked fine.
(yeah I know that I could write Hidden=yes but they were uninstalling files so I didn't care)
Thanks for your help :)

---

