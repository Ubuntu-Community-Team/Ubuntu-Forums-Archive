---
title: "Change user's home directory"
date: 2007-11-13
forum: General Help
---

### Post by herbie_popnecker on 2007-11-13
I have a 7.10 webserver setup and wondered how you set a user's default directory through the command line. Usually I do it through the GUI interface, but what if I want to ssh in and add one.

eg.

I have set up joeblow.server.com
Normally I'd add a user joeblow, set his directory to /var/www/joeblow/web/ with the GUI, then sudo chown -R joeblow:joeblow joeblow.

If I ssh in and adduser joeblow, how do I change his default directory to /var/www/joeblow/web?

ALSO: what is the proper shell to use to give them access to their web folder but not ssh or anything else?

---

### Post by scorp123 on 2007-11-13
> **herbie_popnecker said:**
> I have a 7.10 webserver setup and wondered how you set a user's default directory through the command line.  Check the manual for the "useradd" command: ```
man useradd 
``` You can define the new user's home upon account creation. If the account already exists you can use the "usermod" command (again: check the manual if unsure how to use it) and assign a new home directory.

---

