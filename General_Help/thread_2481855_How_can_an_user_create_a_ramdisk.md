---
title: "How can an user create a ramdisk ?"
date: 2022-12-11
forum: General Help
---

### Post by elfishbear on 2022-12-11
Hello,

The root can create a ramdisk, however can it be done by a regular user ?
(without sudo). 

```

 cd ; mkdir ramdisk ; mount -t tmpfs -osize=950M none   ramdisk  ; mount 

```

Kind regards

---

### Post by TheFu on 2022-12-11
mounts shouldn't be allowed by end-users, ever.  The power to mount is the power to destroy.

But anything is possible if you corrupt the OS sufficiently and allow any user to run commands they normally wouldn't be allowed.  Probably best not to share those steps. It is one of those questions where if you have to ask, then you probably don't understand the ramifications fully. Should an end-user be allowed to crash an entire OS at will?  I'd say no.

---

### Post by elfishbear on 2022-12-11
with chmod +S  for superuser ?

---

### Post by HermanAB on 2022-12-12
It depends 100% on what you use your machine for.  The default installation is highly secure, to prevent novice user problems disrupting the whole LAN.

However, if it is an engineering machine in a laboratory, then you may want to use SUID root on a few utilities to more readily configure the network addressing, routes, vlans and disk mounts.

Some googling will get you going, but bear in mind that the more holes you poke in the system security, the easier it becomes for someone else to disrupt your system.

---

### Post by Doug S on 2022-12-13
/dev/shm exists by default and is available for regular users. It is tmpfs and ram based. I use it as a regular user constantly.

---

