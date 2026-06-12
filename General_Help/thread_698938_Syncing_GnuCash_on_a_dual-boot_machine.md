---
title: "Syncing GnuCash on a dual-boot machine"
date: 2008-02-16
forum: General Help
---

### Post by zoso375 on 2008-02-16
GnuCash is my financial software of choice.  I use it on Ubuntu and XP on a dual-boot machine.  Does anyone know of a way that I can sync GnuCash between partitions?  I would love to be able to access and sync across platforms.  Thanks in advance.

---

### Post by Irihapeti on 2008-02-16
I've not used GnuCash, but I used to sync the Firefox history file between a Windows and Ubuntu installations using rsync, and I think the concept would be the same.

It's several months now since I had a windows installation, but I seem to remember I did something like this:

before opening the program in Ubuntu, rsync the windows file only if it's newer than the Ubuntu copy. On closing the program, copy (rsync) the file to the windows partition. Details on how to do this are in the rsync man page.

Oh, and when you test it, do a backup of your data file first.

---

