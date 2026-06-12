---
title: "Automount LUKS partition on login"
date: 2013-07-17
forum: General Help
---

### Post by CaffeineFreeless on 2013-07-17
I have a LUKS partition at, say, /dev/sdb1 that I'd like auto-mounted at the login of a specific user.Since its decryption password is in the user's keyring, it can be mounted without prompting for a password by clicking the partition in Thunar. I'd basically like to automate that process to happen at login. Security is not an issue since the user's home directory is encrypted, as is the file system itself, so it would require a few levels of passwords to get into to begin with.Any tips on getting that partition mounted at login?

---

