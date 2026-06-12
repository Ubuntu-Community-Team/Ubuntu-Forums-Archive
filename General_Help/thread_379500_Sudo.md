---
title: "Sudo"
date: 2007-03-08
forum: General Help
---

### Post by dgore on 2007-03-08
Just to make sure I don't mess up....

Just installed and logged in with OEM.  When I run the command to get rid of OEM and reboot which make me create a new user...will this user automatically have root access with Sudo?

---

### Post by etank on 2007-03-08
No the new user will not have sudo rights. If you want them to you need to add them to the admin group. That is if you want them to have the same rights as the first user created.

**Ignore this. I did not notice the OEM part. Sorry about that.**

---

### Post by dgore on 2007-03-08
Your answer confused me.  Install creates OEM user, then it says to run something that gets rid of OEM and after reboot it asks you to setup a user.  Does this user have SUDO rights.  I don't want to get locked out of the system.

---

### Post by bapoumba on 2007-03-08
@ dgore: running **sudo oem-config-prepare** will remove the oem user and replace it with a new user that will indeed have sudo access (it will be in admin group).

---

