---
title: "Problms with Java Virtual Machine"
date: 2005-09-08
forum: General Help
---

### Post by caspian on 2005-09-08
I've installed Java on my computer, and the java compiler works fine.

However, something's wrong with my Java Virtual Machine. When I try to execute a java program, I get this message:

> java.lang.UnsupportedClassVersionError
   at java.lang.VMClassLoader.nativeDefineClass (VMClassLoader.java)
   at java.lang.VMClassLoader.defineClass (VMClassLoader.java:96)
   at java.lang.ClassLoader.defineClass (ClassLoader.java:672)
   at java.security.SecureClassLoader.defineClass (SecureClassLoader.java:88)
   at java.net.URLClassLoader.findClass (URLClassLoader.java:833)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:359)
   at java.lang.ClassLoader$1.loadClass (ClassLoader.java:1282)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:303)
   at java.lang.VirtualMachine.main (VirtualMachine.java:83)

Does anyone know what's causing this or what I can do to fix it?

Thank you very much!

---

