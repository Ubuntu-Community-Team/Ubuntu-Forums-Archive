---
title: "gnome logs out when i lock the screen for a whiel"
date: 2008-05-14
forum: General Help
---

### Post by jabirahmed on 2008-05-14
When i take a break i usually lock my screen to make sure i am not loosing any unsaved work 

but surprisingly wen i return i see that Ubuntu has been kind enough to log me out.. closing al the unsaved work... and also closing my browser/pidgin and other xterms that i was using to log into other machines.

This happened only after i ungraded from 7.10 to 8.04..

Is there any solution to this... Is it a bug or Is it an issue with my configuration

Rgds
Jab
[email]jabirahmed@yahoo.com[/email]

---

### Post by hermes0710 on 2008-05-14
Try adding a new user, login and lock. Does this still happen? If no then settings kept by the upgrade mess up gnome.

---

### Post by chrisccoulson on 2008-05-14
Sounds like xorg crashing. When you log back in again, is there a backtrace at the end of /var/log/Xorg.0.log.old?

---

