---
title: "what package a command is in"
date: 2022-05-28
forum: General Help
---

### Post by Skaperen on 2022-05-28
supposedly there is a database set up by apt that given a command name you can get the name of the package it comes in, even if that package is not installed.  does anyone know where that database is at?

---

### Post by #&amp;thj^% on 2022-05-28
I come in peace, so be nice. :P
something like this?
```
apt show gnome-mpv
Package: gnome-mpv
Version: 0.20-2
Priority: optional
Section: universe/video
Source: celluloid
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <debian-multimedia@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 28.7 kB
Depends: celluloid
Homepage: https://github.com/celluloid-player/celluloid
Download-Size: 7,184 B
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: transitional package
 This is a transitional package. It can safely be removed.


```
I forgot this one:
```
dpkg -S /bin/ls
coreutils: /bin/ls

```
You know this, but I'll post it anyway>> The APT package index is basically a database that holds records of available packages from the repositories you have installed/enabled.
if you want to have some fun run this:
```
apt-cache pkgnames
```
best to print that to .txt for better view.
Or a much more friendly way to see: [https://packages.ubuntu.com/](https://packages.ubuntu.com/)

---

### Post by Holger_Gehrke on 2022-05-28
And in addition to that there's an SQLite database populated by apt used by the command-not-found handler (a python script called through a shell-function when the shell encounters a command not found error) that - at least in XUbuntu 22.04 - resides in '/var/lib/command-not-found/commands.db'.

Holger

Edit: the raw data which gets put into this db are the '/var/apt/lists/*Commands-*' files

---

### Post by #&amp;thj^% on 2022-05-28
It is the same location on gnome as well:
```
cd /var/lib/command-not-found/ && ls -a
.  ..  commands.db  commands.db.metadata

```
 good call Holger_Gehrke

---

