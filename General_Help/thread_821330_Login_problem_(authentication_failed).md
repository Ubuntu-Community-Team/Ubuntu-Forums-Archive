---
title: "Login problem (authentication failed)"
date: 2008-06-07
forum: General Help
---

### Post by stefgro on 2008-06-07
If I restart X by pressing ctrl-alt-backspace, I come to the login screen, but a window pops up, saying "Authentication failed" - and I cannot login, because that window won't dissapear.

Trying to fix this, I got problems with the .Xauthority file, which caused me to not being able to run a lot of things/settings in Ubuntu (got the "error locking to authority file /home/(user)/.Xauthority), but I ran chown (username) - and fixed that.

If I turn off automatic login, in the "login window" under "Administration", I cannot log in at the start-up screen, but have to kill X and log in at the command line, and start X afterwards manually.

Any suggestions?

---

### Post by iaculallad on 2008-06-07
After you chown'ed .Xauthority file, re-install your GDM through Synaptics.

---

### Post by stefgro on 2008-06-07
> **iaculallad said:**
> After you chown'ed .Xauthority file, re-install your GDM through Synaptics.

I did, all the packages that I had which appeared when I searched for GDM, I reinstalled.

---

### Post by stefgro on 2008-06-08
Any other ideas?

---

