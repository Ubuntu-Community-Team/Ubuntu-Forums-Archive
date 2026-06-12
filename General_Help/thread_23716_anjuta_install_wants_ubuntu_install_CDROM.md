---
title: "anjuta install wants ubuntu install CDROM??"
date: 2005-04-03
forum: General Help
---

### Post by b7j0c on 2005-04-03
$ sudo apt-get install anjuta
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
anjuta-common libpcre3
Suggested packages:
libgtkmm2.0-dev libgnomemm2.0-dev devhelp-books glade-2 glade-gnome-2
Recommended packages:
automake autoconf autogen ctags devhelp gnome-devel libtool
The following NEW packages will be installed:
anjuta anjuta-common libpcre3
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6628kB/6735kB of archives.
After unpacking 14.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
'Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)'
in the drive '/cdrom/' and press enter



??????

why would i have to insert the OS install media to install this app?

---

### Post by bored2k on 2005-04-03
You have the cdrom in your /etc/apt/sources.list, and the app is already in your disc drive.

---

### Post by b7j0c on 2005-04-03
thank you!

---

