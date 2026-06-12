---
title: "start with clean session"
date: 2007-08-12
forum: General Help
---

### Post by mykrob on 2007-08-12
Hey-

I installed Ubuntu Feisty on my sisters laptop. All hardware and everything works fine. Onlyproblem I am having is that when she starts, OpenOffice opens automatically, as does a file browser.I have unchecked the option to auto-save a session in hopes that it would restart with a default session, but it doesnt..

How do i make it start with a clean session?

Thanks,
-myk

---

### Post by kellemes on 2007-08-12
Remove your Gnome-sessionfile.
I don't use Gnome myself so I don't know where it is, but probably somewhere beneath ~/.gnome2

---

### Post by ajgreeny on 2007-08-12
Open up the gnome-control-center using a terminal if you can't find it in menus, and go to the session icon in that.  There you can disable the startup programs by unchecking them.  Simple.

However, it is worth having a startup item for OO as otherwise it can be very slow the first time.  To do this add an item with the command:-
ooffice -quickstart -nologo -nodefault
and then when you want OO it will start up in about 5 -6 seconds instead of 15 -20.  You will not have an actual OO on the desktop, just the files opened in advance for a faster startup time.

---

### Post by mykrob on 2007-08-12
openoffice and the file browser do not appear in the startup apps.. I am not a Gnome user, so i am not sure about what file to remove either.. can a gnome guru confirm?

Thanks,
-myk

---

### Post by sisco311 on 2007-08-12
> **mykrob said:**
> openoffice and the file browser do not appear in the startup apps.. I am not a Gnome user, so i am not sure about what file to remove either.. can a gnome guru confirm?

Thanks,
-myk


```
rm ~/.gnome2/session 
```i[SIZE=-1]t appears that this is[/SIZE] a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/34321")
sorry but i'm not a gnome guru:)

---

### Post by mykrob on 2007-08-13
thanks :)

---

