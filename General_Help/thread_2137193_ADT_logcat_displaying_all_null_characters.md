---
title: "ADT logcat displaying all null characters"
date: 2013-04-20
forum: General Help
---

### Post by JaySeeJC on 2013-04-20
The ADT logcat output seems to be outputting all null characters (the ones that look like [] ). Any idea why, or better yet what font is missing? I've already copied all the fonts from window$ (C:\Windows\Fonts\*) to my universal fonts folder (/usr/share/fonts/)

Output of console start to finish:
```
adt-eclipse Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed


(ADT:22449): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're its parent.



```

Screenshot: 
[https://dl.dropboxusercontent.com/u/51261980/Snapshots/logcat.png](https://dl.dropboxusercontent.com/u/51261980/Snapshots/logcat.png)

---

