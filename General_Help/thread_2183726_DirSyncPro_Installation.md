---
title: "DirSyncPro Installation"
date: 2013-10-26
forum: General Help
---

### Post by AlexHudghton on 2013-10-26
Trying to install DirSyncPro-1.46-Linux on 12.04

Installed Java

java -version
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.6) (6b27-1.12.6-1ubuntu0.12.04.2)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

running the jar file gives;
$ java -jar dirsyncpro.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: dirsyncpro/DirSyncPro : Unsupported major.minor version 51.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: dirsyncpro/DirSyncPro. Program will exit.


Anyone have a clue? please?

---

### Post by AlexHudghton on 2013-10-26
seems like it needs java 1.7 or above, so why didn't I get the latest when I installed it?

---

### Post by AlexHudghton on 2013-10-27
installed LuckyBackup instead :cool:

---

