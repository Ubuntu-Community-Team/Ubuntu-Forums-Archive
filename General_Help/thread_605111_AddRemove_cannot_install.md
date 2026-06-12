---
title: "Add/Remove cannot install"
date: 2007-11-06
forum: General Help
---

### Post by L815 on 2007-11-06
In the add/remove there are programs which I can't install because it says my processor isn't supported i386.

I find that strange because Bittorrent was installed by default, I uninstalled it and wanted to re-install it to give it a try. But not it says that error (along with many others). 

I wonder why that's so?

---

### Post by taurus on 2007-11-06
I bet because all the repos in /etc/apt/sources.list are commented out, with a # in front.  Post your /etc/apt/sources.list here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by oilchangeguy on 2007-11-06
> **L815 said:**
> In the add/remove there are programs which I can't install because it says my processor isn't supported i386.

I find that strange because Bittorrent was installed by default, I uninstalled it and wanted to re-install it to give it a try. But not it says that error (along with many others). 

I wonder why that's so?

are you sure you installed the 32bit version of ubuntu. and not the 64bit version?

---

### Post by L815 on 2007-11-06
Yah it was because one of my sources was absent (probably accidently deleted it).I used the sources maker from Ubuntu and everything seems OK now. 

I should have checked before starting this thread. -_-

---

