---
title: "Deleted my /etc/modules - need help."
date: 2007-05-06
forum: General Help
---

### Post by electronikjunkie on 2007-05-06
Title says it. What is the default contents of /etc/modules for Feisty on amd64 server install? What is the ownership/permissions?

TK

---

### Post by mlind on 2007-05-06
```

$ ls -la /etc/modules 
-rw-r--r-- 1 root root 331 2007-04-24 01:13 /etc/modules

```

```

$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
fuse

```

This is feisty on x86 32bit though. fuse module was probably added when I installed *ntfs-3g*.

---

### Post by electronikjunkie on 2007-05-06
Thank you. I'll give a whirl and see what happens.

TK

---

