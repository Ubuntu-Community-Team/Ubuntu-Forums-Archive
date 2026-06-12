---
title: "[SOLVED] epiphany icon?"
date: 2008-05-26
forum: General Help
---

### Post by petunia50 on 2008-05-26
Hello,
I recently installed ubuntu 8.04.  firefox 3 beta 5 sometimes locks up.  I downloaded epiphany, but it didn't add an icon to the applications menu.  I seem to remember that I got an icon when I downloaded/installed epiphany with version 7.10.  I know that I can open a terminal & type 'epiphany' to start the app.
My question is:  How do I place an icon or shortcut somewhere so that I do not have to use the terminal in order to start epiphany?
Thank You

---

### Post by Gunman1982 on 2008-05-26
You need to restart the menu so the icon is loaded. Just open a console and execute 'killall gnome-panel' or press alt+F2 and execute 'killall gnome-panel'

---

### Post by drs305 on 2008-05-26
Right click the top or bottom panel, Add to Panel, Custom Application Launcher. 'Application', name it what you want, and in the command 'epiphany'.

Normally you could choose Add to Panel, Application Launcher, and then you would find the app in the list. Since it's not showing in the menus, it probably wouldn't show up here either.  ;-)

If it does show up in the menu, you can always just drag the icon to a panel to create a one-click shortcut.

---

### Post by petunia50 on 2008-05-26
Thank you to Gunman1982.  I followed your instructions & it worked very well.
Thanks to drs305 too.

---

