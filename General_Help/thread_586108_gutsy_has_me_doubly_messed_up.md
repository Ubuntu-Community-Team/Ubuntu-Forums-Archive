---
title: "gutsy has me doubly messed up"
date: 2007-10-22
forum: General Help
---

### Post by NFITC1 on 2007-10-22
Like a few other people, logging in seems to give an endless repeat of reboots. I thought it might have been compiz so I uninstalled that to no avail. Also, when I try to compile something using the -m32 flag in g++ it says
```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++

```

I did an upgrade from feisty via Update Manager and this stuff worked fine in feisty. It SHOULD look at the libstdc++.so.5 or libstdc++.so.6 in /usr/lib32 (this one needs libstdc++.so.5 I think), but it's acting like that's not even there.

---

