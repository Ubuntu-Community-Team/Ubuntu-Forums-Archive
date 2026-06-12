---
title: "Error installing Plugin on libre office &quot;Language tool&quot;"
date: 2019-03-18
forum: General Help
---

### Post by g-baaijens on 2019-03-18
Hello, 

I get this issue when i try to install a plugin in libre office 6.0.
I have updated Ubuntu And Libre office.

Java version:
```
java version "1.8.0_201"
Java(TM) SE Runtime Environment (build 1.8.0_201-b09)
Java HotSpot(TM) 64-Bit Server VM (build 25.201-b09, mixed mode)
```

I redownloaded the plugin a few times.


```
[jni_uno bridge error] UNO calling Java method writeRegistryInfo: non-UNO exception occurred: java.lang.NoClassDefFoundError: com/sun/star/task/XJobExecutor
java stack trace:
java.lang.NoClassDefFoundError: com/sun/star/task/XJobExecutor
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:763)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:468)
    at java.net.URLClassLoader.access$100(URLClassLoader.java:74)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:369)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:363)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:362)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:424)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:411)
    at java.net.FactoryURLClassLoader.loadClass(URLClassLoader.java:817)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:357)
    at com.sun.star.comp.loader.RegistrationClassFinder.find(RegistrationClassFinder.java:53)
    at com.sun.star.comp.loader.JavaLoader.writeRegistryInfo(JavaLoader.java:376)
Caused by: java.lang.ClassNotFoundException: com.sun.star.task.XJobExecutor
    at java.net.URLClassLoader.findClass(URLClassLoader.java:382)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:424)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:357)
    ... 15 more

```

What can i do to solve this issue?

Have i posted this in the right place?

---

