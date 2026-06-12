---
title: "two OS, one workstation"
date: 2007-05-22
forum: General Help
---

### Post by raharris on 2007-05-22
I've installed Wubi on my Win XP workstation and most everything works fine, but I can't access my network drives from the linux side.  I connect to any number of servers for storage, webpages, etc., all of which are running Win 2000 (one is running NT, but I'll ignore that for the time being).  In one case I can log onto another machine using the terminal server, and thqt is fine.  But I'd like to know the best way to access my other network drives.  Samba?  VM Server?  Or can't I just map a drive the way I do on Windows?

Any assistance is appreciated -- RAH

---

### Post by cyrusrayne on 2007-05-24
The most popular way I've seen to access windows files from Linux/Unix has to be samba.  There are many people far more skilled than I in doing this, but I've used samba on the client side and it works rather well (my last job used samba to send documents to the stores).

As you pointed out, there are several different choices out there so the choice is entirely up to you, but my recommendation would be samba.

---

