---
title: "OpenOffice 2 Beta deb package"
date: 2005-10-07
forum: General Help
---

### Post by Elrohir on 2005-10-07
once upon a time, in a thread long long ago, it was posted the link for some guide for installing OOo 2 Beta... anybody remembers or know about this? I want to ditch OOo 1.1.4 and move to OOo 2...;-)

---

### Post by Perfect Storm on 2005-10-07
[http://ubuntuforums.org/showthread.php?t=62316](http://ubuntuforums.org/showthread.php?t=62316)
It's a bit long thread, but go for the script installation instead, or wait some couple ofdays for breezy ;)

---

### Post by raghav_p on 2005-10-07
You should download the tarball from [http://www.openoffice.org/]("http://www.openoffice.org/")

extract it to a location in ur home folder using the GUI.

in terminal, switch to the directory you saved it in. then switch to a folder called RPMS.

then, type in the following:

> sudo alien *.rpm

then,

> sudo dpkg -i *.deb

and then create the menu items if you want. you can open openoffice by 
using: /opt/openoffice.org<1.9.125>/program/soffice.bin

the <1.9.125> might be different in your installation

---

### Post by Elrohir on 2005-10-07
[quote=Artificial Intelligence]wait some couple ofdays for breezy ;)[/quote]already asked shipit for Breezy cds... anyways... I'll download and do as raghav_p says... thats the method I remember... thanx...

---

### Post by Elrohir on 2005-10-08
[quote=raghav_p]and then create the menu items if you want[/quote]of course! how can I do this? :confused:

---

### Post by Matchless on 2005-10-08
[QUOTE=Elrohir]once upon a time, in a thread long long ago, it was posted the link for some guide for installing OOo 2 Beta... anybody remembers or know about this? I want to ditch OOo 1.1.4 and move to OOo 2...;-)[/QUOTE]

Go to the Howtos list, there is an easier way, by downloading the deb files directly and reading them with synaptic and installing. It works!

---

