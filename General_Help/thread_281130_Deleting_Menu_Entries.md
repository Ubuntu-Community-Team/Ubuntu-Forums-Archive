---
title: "Deleting Menu Entries"
date: 2006-10-20
forum: General Help
---

### Post by robcarr2 on 2006-10-20
Is there a default place for where entries in the menu are stored? I installed dvd::rip through Automatix, I uninstalled it through Automatic too but it is still in the menu, all the files for it have been deleted but I am left with the entrie in the menu.

If anyone knows how to get rid of it please share :P

---

### Post by CatKiller on 2006-10-20
Menu entries are usually .desktop files in one of quite a few locations. You can either hunt down the .desktop file that corresponds to the menu entries you don't like, or you could just right-click on the menu, select Edit Menu, find the entry and untick it. Either way the result is the same - you don't see it in your menu.

EDIT: According to the [Ubuntu package search]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=dvdrip&version=dapper&arch=i386"), the file is in /usr/lib/menu, despite the fact that "[As of menu, version 2.1.25, /usr/lib/menu as location for menu files is deprecated (but still works perfectly). Menu files should now be placed in /usr/share/menu instead. Only menu files that are actually binary executables still need to go to /usr/lib/menu.]("http://lintian.debian.org/reports/Tmenu-file-in-usr-lib.html")"

---

### Post by arnieboy on 2006-10-20
> **robcarr2 said:**
> Is there a default place for where entries in the menu are stored? I installed dvd::rip through Automatix, I uninstalled it through Automatic too but it is still in the menu, all the files for it have been deleted but I am left with the entrie in the menu.

If anyone knows how to get rid of it please share :P

try doing ```
sudo rm -f /usr/share/applications/dvdrip.desktop
```

---

### Post by robcarr2 on 2006-10-21
I didnt think of just unticking it >.<

Thanks :)

---

