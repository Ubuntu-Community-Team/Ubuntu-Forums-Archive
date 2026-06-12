---
title: "Is there a preconfigured administrator Account?"
date: 2007-04-23
forum: General Help
---

### Post by dfarce on 2007-04-23
I accidentally made my default Ubuntu account a non administrator and set it to automatically log in. Now I can't change anything. Is there any way to get back Administrator privileges? Maybe a preconfigured account that you can log into with the right username and password to change the settings? I'm running a liveUSB of Linux.

---

### Post by bwhite82 on 2007-04-23
A root account is installed by default but disabled. You can use 'sudo' to give yourself 'super-user' (root) priveledges to accomplish what you need to.

---

### Post by az on 2007-04-23
> **dfarce said:**
> I accidentally made my default Ubuntu account a non administrator and set it to automatically log in. Now I can't change anything. Is there any way to get back Administrator privileges? Maybe a preconfigured account that you can log into with the right username and password to change the settings? I'm running a liveUSB of Linux.

Boot into recovery mode and create a user.  Add that user to the admin group.

---

### Post by dfarce on 2007-04-27
You CAN boot into safe mode using a persistent install, but it loses the "persistent" feature and you can't edit any of your settings. I think I might have to wipe my casper-rw folder. Do you think that this woulod wreck my installation or just wipe the preconfigured accounts?

---

