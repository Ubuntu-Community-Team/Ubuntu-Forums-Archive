---
title: "Allow user to install, but not remove software"
date: 2008-03-08
forum: General Help
---

### Post by pofigster on 2008-03-08
I don't know if this is possible, but can I define the rights of a user on my computer to be allowed to install software, but not uninstall software?  I don't want my son to be able to uninstall the web filter and proxy software, but I don't want to have to peer over his shoulder everytime he wants to install a new game or something.

---

### Post by pointone on 2008-03-08
You can do this with apt-get by editing the sudoers file:

```
username    ALL = (root) /usr/bin/apt-get install !/usr/bin/apt-get remove
```

Not sure how you could do this for Synaptic, though.

---

