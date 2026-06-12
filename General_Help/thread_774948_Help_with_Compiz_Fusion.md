---
title: "Help with Compiz Fusion"
date: 2008-04-29
forum: General Help
---

### Post by Shadius on 2008-04-29
Hi, I'm new to Ubuntu so bare with me. Upon installing Ubuntu 8.04 from 7.10 I installed "ccsm". However, I found a thread here, about getting all compiz plugins using git, now I don't know what "git" is, but I read the plugin and alot of the users had success with it, so I tried it out and didn't like it. Removed it using the instruction from the same thread. Then I tried getting "ccsm" again, and I get errors. I need help getting back Compiz Fusion. Please help!!!

---

### Post by Zorael on 2008-04-29
Quoting myself from another thread.
> **Zorael said:**
> Can't promise you it'll work, but try this.
```
$ sudo aptitude purge ~ncompiz ~nemerald ~nlibdeco
$ sudo aptitude update
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```

---

