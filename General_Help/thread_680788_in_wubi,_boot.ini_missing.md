---
title: "in wubi, boot.ini missing"
date: 2008-01-28
forum: General Help
---

### Post by buckykat on 2008-01-28
i'm trying to install ubuntu on an old windows 2000 machine, but i am obliged to change it as little as possible. i tried wubi, because it claimed it didn't need any partitioning. when i rebooted, nothing was changed. no grub showed up at all. it just booted normally. i searched around to find out what's wrong. it seems that i should see three files at c:\ wubildr, wubildr.mbr and boot.ini. the first two are present, but boot.ini is not there at all.

---

### Post by ago on 2008-01-28
It's probably hidden. You need to have the rights to edit that file.

---

### Post by buckykat on 2008-01-28
that still leaves the problem of ubuntu not showing up at all. the installer seemed to work fine.

---

### Post by ago on 2008-01-28
If you have no permission to edit boot.ini, wubi would not be able to do that either

---

### Post by nitrofurano on 2009-03-12
in my case, there's no c:\boot.ini at all - where else may be this file, and with which name?  it's a dualboot with Vista... (i were just helping a friend to progressivelly replace Vista with Ubuntu)

---

