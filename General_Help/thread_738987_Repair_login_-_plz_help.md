---
title: "Repair login - plz help"
date: 2008-03-29
forum: General Help
---

### Post by Ubundood on 2008-03-29
I installed pam-keyring and after that, whenever i booted my computer i got a message in the login window saying "Authentication failed", not being able to log in anyway.

I uninstalled pam-keyring but the problem persisted.

In recovery mode, i deleted the whole etc/pam.d directory. The "Authentication failed" message is still there.

Anyone has an idea on how to repair the whole Ubuntu login?

Thanks

---

### Post by pointone on 2008-03-29
Uh... removing /etc/pam.d certainly wasn't the best choice. You'll need to reinstall PAM somehow to get this directory back. PAM handles all authentication for your system, and /etc/pam.d contains the configuration files for PAM. Without it, you won't be able to log in at all.

Try "apt-get --reinstall install libpam-runtime". If you're still having problems logging in afterwards, post the contents of /etc/pam.d (i.e. "ls /etc/pam.d") and check /var/log/auth.log for error messages.

---

