---
title: "[SOLVED] Javac compiles, but Java returns error unrelated to code"
date: 2008-06-27
forum: General Help
---

### Post by AkuTenshi on 2008-06-27
[COLOR="Red"]SOLVED: Removed package declaration at beginning of class[/COLOR]

When I code a java application, it compiles fine. When it try to run it however ('java Main'), it returns an error that is nonspecific to the application. 
```

ross@ross-ubuntu:~/NetBeansProjects/bashtest/build/classes/bashtest$ java Main
Exception in thread "main" java.lang.NoClassDefFoundError: Main (wrong name: bashtest/Main)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:637)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)

```
For some reason, code run by NetBeans works. Java -version reuturns
```

java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)

```
Which is strange because Synaptic says that JDK is version 6.

Any Help?

---

### Post by andrewc6l on 2008-06-27
You're compiling a class called bashtest.Main, but then trying to run it as Main.

Try:
cd ~/NetBeansProjects/bashtest/build/classes
java bashtest.Main

Also, version 1.5 = Java 5; version 1.6 = Java 6.

---

### Post by AkuTenshi on 2008-06-28
The project (under netbeans) is called bashtest, but the class is called Main, and when compiled produces Main.class. Java also gives the same error whether the file exists or not, which makes me think I may be putting in the filename incorrectly. 

Thanks for explaining the version numbers.

---

