---
title: "Proper Way to stop apache2 from being started at boot time"
date: 2005-08-10
forum: General Help
---

### Post by phibuntu on 2005-08-10
Whenever I start Ubuntu, Apache2 is started as well.
I use Apache only for tests before going online. So I want to start it manually and stop it manualy.

What is the proper way to tell Ubuntu, that apache should not be started at boot time? Is there a config tool like in SuSE (YaST2) for that?

---

### Post by flyinglizard on 2005-08-10
I believe the update-rc.d command the the correct method to do this.  You can find more information in the man page,  or search the forums.

update-rc.d -f <name> remove

---

### Post by phibuntu on 2005-08-12
Thanks. That was the point.

as an old SuSE freak i was looking for something like a runlevel-editor ;-)

---

