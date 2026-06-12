---
title: "missing  libstdc++-libc6.2-2.so.3"
date: 2007-06-24
forum: General Help
---

### Post by yinglcs2 on 2007-06-24
hi, 
I get this error when I run a linux program, can you please tell me how can I fix it?

error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Thanks.

---

### Post by yinglcs2 on 2007-06-24
I try the suggestion described here:

[http://www.digitalsanctum.com/2007/01/28/libstdc-libc62-2so3-on-ubuntu/](http://www.digitalsanctum.com/2007/01/28/libstdc-libc62-2so3-on-ubuntu/)

But it can't find the package:

```
$ sudo apt-get install libstdc++2.10-glibc2.2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++2.10-glibc2.2
```

---

### Post by WW on 2007-06-24
That package is in the universe [repository]("https://help.ubuntu.com/community/Repositories/Ubuntu").   Have you enable this repository?

---

