---
title: "Installing apps on wubi"
date: 2008-05-21
forum: General Help
---

### Post by hampshire_tux on 2008-05-21
hi all,
i've got a pc with Windows XP as the main OS,and linux booting through Wubi.
i was wondering if anyone can tell me if you can install apps on a Wubi booted linux and where the apps go(so i can boot them)
PS:the distro im using is Ubuntu 8.04

---

### Post by ago on 2008-05-21
apps will go into the Ubuntu filesystem in the appropriate directories (generally /usr/bin /usr/share /usr/lib...)

they are not available from within windows since the Ubuntu filesystem is encapsulated within a single windows file.

some apps will appear in the menu, others you can access as a command (and optionally create shortcuts for the menu/desktop/toolbar)

---

### Post by hampshire_tux on 2008-05-21
> **ago said:**
> apps will go into the Ubuntu filesystem in the appropriate directories (generally /usr/bin /usr/share /usr/lib...)

they are not available from within windows since the Ubuntu filesystem is encapsulated within a single windows file.

some apps will appear in the menu, others you can access as a command (and optionally create shortcuts for the menu/desktop/toolbar)


still cant find the app in linux but thanks

---

### Post by ago on 2008-05-21
open a terminal (or alt+f2) and simply type the app name. So if you installed "firefox" just type in... "firefox"

most apps will be either in /usr/bin or in /usr/local/bin

---

### Post by twright on 2008-05-21
i think you are looking for the applications menu and add and remove programs

---

