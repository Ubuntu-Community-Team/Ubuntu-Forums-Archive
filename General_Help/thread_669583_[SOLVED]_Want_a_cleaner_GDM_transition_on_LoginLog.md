---
title: "[SOLVED] Want a cleaner GDM transition on Login/Logout"
date: 2008-01-16
forum: General Help
---

### Post by Arthur Archnix on 2008-01-16
Some time ago someone had pointed out to me that there was a way to edit the order in which files were executed on logging into, and out of, gnome. Currently, when I boot up my system I see the following:

1. Grub text
2. Usplash
3. Black screen with large text output related to network manager
4. Some mode switches as 'x' loads
5. GDM

It would be a lot nicer looking if I could make that network manager stuff disappear, in fact, I don't recall seeing it before I ran some recent updates. Is there a way to invoke the gdm sooner so that the terminal text about network manager is hidden? 

When logging out of my gnome session, it also shows me some network stuff before the gdm. And again, I'm pretty sure someone told me how to fix this by invoking the GDM sooner in the logout process, but I can't find the info anymore. Currently it goes:

1. Hit logout button
2. Black screen with large text output related to network manager
3. GDM. 

Tips & Help greatly appreciated,

---

### Post by Arthur Archnix on 2008-01-18
Bump.

---

### Post by Arthur Archnix on 2008-01-19
Bump 2 of 3.

---

### Post by Arthur Archnix on 2008-01-21
Bump 3 of 3.

---

### Post by Arthur Archnix on 2008-02-27
A reinstall, then full updates fixed it.

---

