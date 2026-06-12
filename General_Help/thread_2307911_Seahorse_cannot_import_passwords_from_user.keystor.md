---
title: "Seahorse: cannot import passwords from user.keystore file"
date: 2015-12-29
forum: General Help
---

### Post by cogset on 2015-12-29
I'm trying to import my passwords (just passwords, not GPG keys) stored in Seahorse from an older Ubuntu installation to Ubuntu 15.04 (MATE version) : given that to date (to the best of my limited knowledge) there is no option in Seahorse to import passwords, I've just tried to overwrite in Ubuntu 15.04 the current* user.keystore *file located in** ~/.local/share/keyrings** with the older file located in **~/.gnome2/keyrings** in the other older OS: however, that isn't working at all.

No passwords in fact show up in Seahorse 3.15.90 even after logging in again and/or rebooting, and also as a side effect the Gnome keyring in Seahorse itself cannot be unlocked any longer (although I don't quite understand the purpose of this Gnome keyring in Seahorse) .
Restoring the previously backed up user.keystore allows me to unlock the Gnome keyring again -but other than that I'm stuck, I can't see a way to import my passwords in this new installation.

Am I doing something wrong here?
Wasn't manually overwriting the current user.keystore file with the older one the commonly agreed upon method to import passwords in Seahorse, for the lack of a better option?
Do I really have to manually enter all my saved passwords in Seahorse in the new OS?

---

### Post by cogset on 2016-01-07
Is the current  Seahorse version just incompatible with older versions, at least as far as stored passwords go?

If so, is there a way around this?

---

