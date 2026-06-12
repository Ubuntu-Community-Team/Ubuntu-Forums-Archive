---
title: "depmod Bus error"
date: 2015-09-10
forum: General Help
---

### Post by Fred_Snertz on 2015-09-10
I am having a problem compiling VmWare on Ubuntu 14.04 LTS.  I believe I have traced it as far as this error:

```
root@fred:~# depmod -a
Bus error (core dumped)
```

I am fully patched and updated.  Any advice on how to fix this?  Thank you.

```
root@fred:~# depmod --version
kmod version 15
root@fred:~# uname -a
Linux fred 3.13.0-63-generic #103-Ubuntu SMP Fri Aug 14 21:42:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

