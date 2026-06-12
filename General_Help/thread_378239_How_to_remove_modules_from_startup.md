---
title: "How to remove modules from startup?"
date: 2007-03-07
forum: General Help
---

### Post by Dr-ROX on 2007-03-07
I'm running ubuntu server 6.10 on pretty old machine and dont want several modules to eat up RAM (64 Megs all I have). Rmmod on runtime does the job, but after reboot all needless  modules are loaded again. 
So how can I remove them from startup?

---

### Post by Dr. Nick on 2007-03-07
I forgot the exact file maybe /etc/modules/blacklist or something.

The term you are looking for is "blacklist module" If you search that you should see the specifics

---

### Post by Dr-ROX on 2007-03-07
Thanks for that idea! I found that file here:

```
/etc/modprobe.d/blacklist
```

---

### Post by watson540 on 2007-03-07
also to tune what services are initialized during boot you can use the package sysv-rc-conf
:)

---

