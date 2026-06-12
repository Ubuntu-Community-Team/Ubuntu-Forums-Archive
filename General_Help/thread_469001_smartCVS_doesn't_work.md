---
title: "smartCVS doesn't work"
date: 2007-06-09
forum: General Help
---

### Post by KIAaze on 2007-06-09
I can't run smartCVS anymore. :(
I get the following error when trying to run it:

> >./smartcvs.sh
Warning: /bin/java does not exist


java.lang.NullPointerException
   at java.lang.VMClassLoader.defineClass(libgcj.so.71)
   at java.lang.ClassLoader.defineClass(libgcj.so.71)
   at java.security.SecureClassLoader.defineClass(libgcj.so.71)
   at java.net.URLClassLoader.findClass(libgcj.so.71)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.71)
   at java.lang.ClassLoader.loadClass(libgcj.so.71)
   at java.lang.ClassLoader.loadClass(libgcj.so.71)
   at java.lang.VMClassLoader.defineClass(libgcj.so.71)
   at java.lang.ClassLoader.defineClass(libgcj.so.71)
   at java.security.SecureClassLoader.defineClass(libgcj.so.71)
   at java.net.URLClassLoader.findClass(libgcj.so.71)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.71)
   at java.lang.ClassLoader.loadClass(libgcj.so.71)
   at java.lang.ClassLoader.loadClass(libgcj.so.71)
   at SmartCVS.main(SourceFile:12)


It's version 6.0.1.

---

