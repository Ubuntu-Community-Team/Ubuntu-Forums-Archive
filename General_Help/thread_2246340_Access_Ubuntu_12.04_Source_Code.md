---
title: "Access Ubuntu 12.04 Source Code"
date: 2014-09-30
forum: General Help
---

### Post by mahmoud7 on 2014-09-30
Hello,
I have Installed Ubuntu 12.04 on a Vmware, i need to access its source code (not the kernel).
what is the commands to do this?
also can i see the main directories in the source code?
any help please?

---

### Post by deadflowr on 2014-09-30
Download it.
```
cd Downloads
apt-get source <packagenamehere>
```

Changed packagenamehere to which ever package source you want to look at.
Ubuntu isn't made of one big source code, but many smaller packages.
The kernel being one of them.

Edit: Adding, by default Ubuntu enables the source repositories, but if you have disable them, you will need to re-enable them.

---

