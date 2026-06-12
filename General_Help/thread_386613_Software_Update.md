---
title: "Software Update"
date: 2007-03-17
forum: General Help
---

### Post by ziffnabb on 2007-03-17
I have a software update that cannot be authenticated.  It is for Automatix2.  It is supposed to be an update from 1.1-2.24-6 to 1.1-2.25-6

Should I ignore it?  If so, can I get rid of the update so it does not always appear on the list?

Thanks,
Ziffnabb

---

### Post by zvacet on 2007-03-17
You can not authenticated Automatix bacause PUBLIC KEY IS MISSING.
Example:missing public key123456
 gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -



 gpg --keyserver hkp://subkeys.pgp.net --recv-keys 123456
 gpg --export --armor 123456 | sudo apt-key add -

---

### Post by ziffnabb on 2007-03-17
So how can I tell what key is missing?

This has never happened before.

Ziffnabb

---

### Post by jackrobinson on 2007-03-17
> **ziffnabb said:**
> So how can I tell what key is missing?

This has never happened before.

Ziffnabb
do this:
```
sudo apt-get update
sudo apt-get upgrade
```
that will upgrade automatix to the latest version (ignore the key errors)
Run automatix and it will automatically add the missing GPG key and you will not get this error in future.

---

