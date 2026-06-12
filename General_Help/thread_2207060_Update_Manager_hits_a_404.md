---
title: "Update Manager hits a 404"
date: 2014-02-21
forum: General Help
---

### Post by Rocket J Squirrel on 2014-02-21
Update Manager has some 42 updates it would like to do but it can't, giving a "Failed to download package files" error. Specifics:

```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.336ubuntu0.12.04.1_i386.deb 404  Not Found [IP: 91.189.92.201 80]
```

But apt-get update and apt-get upgrade don't run into a problem. I saw scrolling by:

Setting up flashplugin-installer (11.2.202.341ubuntu0.12.04.1) ...

So . . . I am not sure why Update Manager seems unhappy.

---

### Post by ian-weisser on 2014-02-21
Repositories (and mirrors) need occasional maintenance and updates, too.
Give it few minutes and try again.

---

