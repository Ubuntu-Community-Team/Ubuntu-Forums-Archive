---
title: "Sun JDK Error"
date: 2006-11-23
forum: General Help
---

### Post by jrobinson5 on 2006-11-23
First of all, i'm using dapper.

Secondly, I'm trying to get the Sun JDK to work. I uninstalled GIJ and installed the JDK and the JRE. Whenever I try to compile a perfectly valid file that works fine on my windows box, I get this:

```
jrobinson@laptop:~/java$ javac p01a.java
jrobinson@laptop:~/java$ java p01a
Exception in thread "main" java.lang.UnsupportedClassVersionError: p01a (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
jrobinson@laptop:~/java$

```

Any ideas on what to do?

---

### Post by taurus on 2006-11-23
What's the output of this command?

```
java -version
```

---

### Post by jrobinson5 on 2006-11-24
```
jrobinson@laptop:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
jrobinson@laptop:~$

```

---

### Post by jrobinson5 on 2006-11-25
Nevermind, i did sudo update-alternatives --config java and it works great.

---

