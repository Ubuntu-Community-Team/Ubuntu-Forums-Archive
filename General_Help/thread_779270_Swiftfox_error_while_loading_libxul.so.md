---
title: "Swiftfox: error while loading libxul.so"
date: 2008-05-02
forum: General Help
---

### Post by gasull2 on 2008-05-02
I updated Swiftfox and now it doesn't start.  If I run swiftfox, I get Firefox instead (!).  So I tried directly with swiftfox-bin:

> 
$ /usr/lib/swiftfox/swiftfox-bin 
/usr/lib/swiftfox/swiftfox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory
$ ls -la /usr/lib/swiftfox/libxul.so 
-rwxr-xr-x 1 root root 17098704 2008-04-27 10:17 /usr/lib/swiftfox/libxul.so


I've already tried to reinstall both Swiftfox and Firefox.

---

