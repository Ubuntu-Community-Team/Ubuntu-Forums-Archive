---
title: "Gnome-Keyring and Subversion"
date: 2014-06-06
forum: General Help
---

### Post by mr-gary-waters on 2014-06-06
So I have read many forum posts and google searches, and I am not able to get my gnome-keyring and subversion to play together correctly.

What I want is subversion to store its passwords into the gnome-keyring, so I dont have non-encrpyted passwords on the local disk.

```
Configs:
.subversion/server
[global]
store-passwords = yes

.subversion/config
[auth]
password-stores = gnome-keyring
```

Gnome keyring is running, but one big thing I have noticed that forums mention, the environmental variable called gnome_keyring_socket, which I do not have.  Here is what I do have:
```
env | grep -i keyring
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-UnZhuf
GNOME_KEYRING_PID=3582
```

I am running Ubuntu 13.10.

Thanks for your help.
-Gary

---

