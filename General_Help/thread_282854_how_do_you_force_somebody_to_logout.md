---
title: "how do you force somebody to logout?"
date: 2006-10-23
forum: General Help
---

### Post by jsmidt on 2006-10-23
Somebody forgot to log out.  I can log in and am the superuser, but how do I force them to logout?  Their screen is locked.

---

### Post by CatKiller on 2006-10-23
I don't know a nice way to do it, but if you've got physical access to the machine, a quick and nasty method is to use **Ctrl**-**Alt**-**Backspace** to kill the X server. Otherwise, if you're ssh'd in from a different machine, a ```
sudo /etc/init.d/gdm restart
``` might work. Haven't ever tried that though.

---

### Post by taurus on 2006-10-23
What if somebody logs into your machine over ssh and you have a physical access to your machine, restarting X is not going to log that user off unless you reboot.  Therefore, you need to run "ps -A" and kill the shell that user is running...

---

### Post by CatKiller on 2006-10-23
Cool. I've learned something interesting today, and met my quota. Thanks, taurus.

---

### Post by taurus on 2006-10-23
> **CatKiller said:**
> Cool. I've learned something interesting today, and met my quota. Thanks, taurus.
No problem but the next one is going to cost you, BIG...  :mrgreen:

---

