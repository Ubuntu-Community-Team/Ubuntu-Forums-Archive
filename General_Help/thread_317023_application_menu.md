---
title: "application menu"
date: 2006-12-11
forum: General Help
---

### Post by random guy on 2006-12-11
hey i am sure others have become annoyed with the fact that some prgrams after isntalled are not shown in the applications menu.  i know that you can manually enter things in but that can be a pain especially when you have to find the location of some of the programs and need to find icons.

is there a more advanced gnome menu editor that i can tell to scan my system for installed apps and load icons and then i can deselect the few that i dont want there with the normal menu editor.

thanks for the help.

---

### Post by bodhi.zazen on 2006-12-11
> **random guy said:**
> is there a more advanced gnome menu editor that i can tell to scan my system for installed apps and load icons and then i can deselect the few that i dont want there with the normal menu editor.

thanks for the help.

There are other menu editors, configuration programs. None work the way you are asking and none will pick up all your installed programs.

The current process is not so bad....

In a terminal type```
whereis <program>
```To find the location (where <program> is the name of the program [application])

Add a menu item or launcher with the full path (it is as easy as cut and paste ...)

HTH

---

### Post by mcduck on 2006-12-11
There is 'menu' package in repos which will add a Debian-menu inside your Applications menu. It should show about all apps you have installed. But I'm not sure if it was enough to just install the package or did it require running some command to populate the menu.

Anyway, since Ubuntu 5.10 I think I have installed 1 or 2 graphical apps that didn't show in the menu automatically. And as most of the times the executable for user-installed apps is in /usr/bin and icon in /usr/share/pixmaps or /usr/share/icons I don't see any serious problem here..

---

### Post by random guy on 2006-12-12
> whereis <program>

never knew that one, ya that will come in handy.  thing is synoptic lists all the programs i have installed anyway so i thought (actually there should really be) a program that will utilize that information that is already present in a contructive way.  

> There is 'menu' package in repos which will add a Debian-menu inside your Applications menu. It should show about all apps you have installed. But I'm not sure if it was enough to just install the package or did it require running some command to populate the menu.

i will look into that some, thanks.  if there is a command to populate i will edit this with it so others will see.

thanks for the help you two.

---

