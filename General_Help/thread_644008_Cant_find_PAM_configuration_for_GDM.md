---
title: "Cant find PAM configuration for GDM"
date: 2007-12-18
forum: General Help
---

### Post by medha on 2007-12-18
Hi!

I keep getting this error, Any help?

Thanks!

---

### Post by stump138 on 2007-12-18
first thing I would do is see if the file /etc/pam.d/gdm is missing.  I'm looking right now to see what package installs that one.

You can try the following pacakges

```
sudo apt-get update && sudo apt-get install libpam-ldap
```


or you can re-create the default /etc/pam.d/gdm file with the following text inserted

```
sudo nano /etc/pam.d/gdm
```

cut and paste..w/e makes you happy
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so  auto_start
@include common-password
```

---

### Post by medha on 2007-12-18
I  have the same error, I am trying to figure out a way..

I think the pam modules are installed with the libpam-modules package.

---

