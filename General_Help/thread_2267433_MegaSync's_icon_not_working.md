---
title: "MegaSync's icon not working"
date: 2015-03-01
forum: General Help
---

### Post by markodd on 2015-03-01
Hey there,

MegaSync's icon is not working. I think it might be the same problem that dropbox had.

Anyone using megasync found a solution?

My OS: xubuntu 14.04

---

### Post by bapoumba on 2015-03-01
Dropbox and Mega work well on my lubuntu 14.10. I'm currently on 15.04 and Mega for ubuntu 14.10 cannot configure, that was expected and I have not looked into it. 

Which flavor are you running ?

---

### Post by markodd on 2015-03-01
> **bapoumba said:**
> Dropbox and Mega work well on my lubuntu 14.10. I'm currently on 15.04 and Mega for ubuntu 14.10 cannot configure, that was expected and I have not looked into it. 

Which flavor are you running ?

I'm on Xubuntu 14.04.02. By "not working" I mean that there's no icon at all. If I type "megasync" in the shell, I get the following:

[18:15:29][warn] QT Warning: QFile::open: File (/home/markodd/.local/share/data/Mega Limited/MEGAsync/megasync.lock) already open

I've no idea what to do, and this is kind of important. damn.

---

### Post by bapoumba on 2015-03-01
Hmm, may be that is xubuntu specific ?
I went back to my Megasync install problem on 15.04 and could finally install. It just finished updating. The copy.com icon I have issues with :)
How did you install Mega ?
You could move the .local/share/data/Mega Limited/MEGAsync/megasync.lock file into another place (your desktop for ex) and see if that clears the error.

---

### Post by markodd on 2015-03-01
Deleting the megaync.lock folder does make the icon appear. However, it only helps until the next restart. That is, as soon as I restart, there's no icon again. I think deleting the megasync.lock file before opening megasync (after every restart) should work.

How do I go about creating a startup command that deletes that file before running "megasync"?

---

### Post by bapoumba on 2015-03-01
You should not need to delete the lock. May be reinstall MegaSync ? How did you install it in the first place ?

---

