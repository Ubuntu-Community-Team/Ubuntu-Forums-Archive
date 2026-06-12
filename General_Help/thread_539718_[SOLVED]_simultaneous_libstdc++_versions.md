---
title: "[SOLVED] simultaneous libstdc++ versions?"
date: 2007-08-31
forum: General Help
---

### Post by TJP on 2007-08-31
I'm trying to run an application (Mathematica) on my Debian system. It keeps looking for libstdc++5, but the distro came with version 6, and it crashes. Can I safely install version 5 alongside 6 without screwing something up?

---

### Post by PaulFr on 2007-08-31
You mean, like this:```
lrwxrwxrwx 1 root root      18 2007-04-20 08:16 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root  737416 2007-01-03 12:22 /usr/lib/libstdc++.so.5.0.7
lrwxrwxrwx 1 root root      18 2007-04-20 05:33 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.8
-rw-r--r-- 1 root root  929648 2007-03-02 18:51 /usr/lib/libstdc++.so.6.0.8
```Yes, there is no problem if the libraries are named properly.

Look at output of ```
aptitude search libstdc++
``` for the list of packages you can install.

Even if you have to have two different variations of the same library, you can do this in any Unix by saving off the variant in another directory, then using LD_LIBRARY_PATH environment variable (**man ld.so** or google for details) appropriately.

---

