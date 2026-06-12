---
title: "update cd"
date: 2007-02-11
forum: General Help
---

### Post by 21_adam_12 on 2007-02-11
hi i was just wondering if there was a way to create an update cd for ubuntu. i need to create an update cd for ubuntu so i can update all my office computers using this cd thus saving bandwidth.

---

### Post by nyinge on 2007-02-11
I'm not sure about a cd with updates, but look into "apt-proxy" to update multiple computers with minimal bandwidth usage.

In a nutshell, you'll configure a machine to act as a package caching server.  So, whenever a networked computer makes an attempt to install a package, that package will be chached in the server.  Any subsequent attempt made for the same package by another machine, the cached package will be used instead of downloading it from the Ubuntu repos.

Note that apt-proxy(package) is in the universe repo.

---

