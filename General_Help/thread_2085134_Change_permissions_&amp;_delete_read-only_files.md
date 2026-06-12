---
title: "Change permissions &amp; delete read-only files"
date: 2012-11-17
forum: General Help
---

### Post by paulemony on 2012-11-17
Ubuntu 11.10
I have some DVD+RWs with old files I want to delete but they are read-only file system & I can't move to rubbish bin, if I go into Properties/permissions I see my username as owner but if I change Access to read and write I get error message telling me I can't as they're read-only. I've tried gksudo nautilus and **sudo rm -rf** in terminal but I still get the same message. Also tried **mount -l** to find partition name (/dev/sr0) & then **sudo mount -o remount,rw /dev/sr0** but just got **mount: warning: /media/filename seems to be mounted read-only.** Possibly there'a a chmod entry but I tried reading the documentation & gave up trying to understand it!:

 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Is there a simple way to get rid of them?

---

### Post by dino99 on 2012-11-17
as i understand, these files have been burned with their attribute; that is.

---

### Post by paulemony on 2012-11-17
Guess what, Brasero Disc Burner doesn't care about read-only file system, just open Tools/Blank & it wipes DVD in a few seconds! Case closed.

---

