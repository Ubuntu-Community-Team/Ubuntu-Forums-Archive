---
title: "Java Game on Linux"
date: 2015-12-21
forum: General Help
---

### Post by Ninko on 2015-12-21
Hello, I am trying to play this game implemented in java which one accesses through a login client (x86_64), this is the error that is thrown on runtime:  ```
Exception in thread "Thread-0" java.lang.UnsupportedClassVersionError: com/client : Unsupported major.minor version 52.0 	at java.lang.ClassLoader.defineClass1(Native Method) 	at java.lang.ClassLoader.defineClass(ClassLoader.java:800) 	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142) 	at java.net.URLClassLoader.defineClass(URLClassLoader.java:449) 	at java.net.URLClassLoader.access$100(URLClassLoader.java:71) 	at java.net.URLClassLoader$1.run(URLClassLoader.java:361) 	at java.net.URLClassLoader$1.run(URLClassLoader.java:355) 	at java.security.AccessController.doPrivileged(Native Method) 	at java.net.URLClassLoader.findClass(URLClassLoader.java:354) 	at java.lang.ClassLoader.loadClass(ClassLoader.java:425) 	at java.lang.ClassLoader.loadClass(ClassLoader.java:358) 	at com.danny.launcher.LauncherFrame.a(Unknown Source) 	at com.danny.launcher.LauncherFrame.ru
```  I've done some research and found that the client may have been compiled on a java version that is not compatible with the one that was installed. Downgrading to ```
openjdk-6-jre openjdk-6-jdk
``` from ```
openjdk-7-jre openjdk-7-jdk
``` has not helped and the issue is present across multiple similar clients for this particular game.  Any ideas?

---

