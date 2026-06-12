---
title: "GDM and KDM broken :confused:"
date: 2007-03-05
forum: General Help
---

### Post by guitarmaniac on 2007-03-05
Ever since installing kubuntu-desktop over my ubuntu I've been having problems with gdm and kdm.
I've tried ```
dpkg-reconfigure kdm
```
and ```
dpkg-reconfigure gdm
```
and it didnt help.
Whenever I started my computer up, it took me to a terminal login and when I typed startx, it logged me into GNOME, when I wanted KDE.
So, stupidly I uninstalled both gdm and kdm (selecting completely remove), planning on reinstalling kdm afterwards, and when I tried to reinstall it I got this message.
> luke@swan-desktop:~$ sudo apt-get install kdm
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdm: Depends: kdebase-bin (= 4:3.5.5-0ubuntu3) but 4:3.5.5-0ubuntu3.2 is to be installed
E: Broken packages
I need help cause I know if I log out I'll have one hell of a time trying to log back in again.
WHAT DO I DO

---

### Post by scxtt on 2007-03-05
can you install xdm in the interm?

btw, both gdm and kdm would be able to log you into either KDE or Gnome (or any other installed DE) ...

---

### Post by guitarmaniac on 2007-03-05
I know both KDM and GDM will log me into either GUI, but neither were working. Thats the problem, will try xdm (but I would prefer KDM if I can get it working).

---

### Post by scxtt on 2007-03-05
if you create a ~/.xinitrc file and put something like:

[indent]#!/bin/bash #not sure if that's needed

gnome-session (for Gnome)
startkde (for KDE)[/indent]

that should solve the problem now matter what *dm you're using ... not entirely sure, but worth a try (after reading the man page on **startx**) ...

---

### Post by guitarmaniac on 2007-03-05
ok, I installed xdm and restarted the computer.
it worked but had no session options or anything.
after logging in I tried installing gdm again and that worked, however kdm is still having unresolved dependancy problems.
I would like to fix this.

---

