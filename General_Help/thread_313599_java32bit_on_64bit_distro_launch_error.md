---
title: "java32bit on 64bit distro launch error"
date: 2006-12-06
forum: General Help
---

### Post by flapane on 2006-12-06
I can't launch any java program because I obtain this (I use the 32bit java version for use it with firefox and flash 32bit, no problems with java firefox plugin):

flapane@a64:~/Desktop$ java javafoil.jar

Exception in thread "main" java.lang.NoClassDefFoundError: javafoil.jar
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: javafoil.jar not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

flapane@a64:~/Desktop$ java --version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
flapane@a64:~/Desktop$

---

### Post by flapane on 2006-12-07
bump

---

