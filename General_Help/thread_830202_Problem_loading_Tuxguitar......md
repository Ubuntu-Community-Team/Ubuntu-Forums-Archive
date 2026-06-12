---
title: "Problem loading Tuxguitar....."
date: 2008-06-15
forum: General Help
---

### Post by morbid_bean on 2008-06-15
Tux guitar will not load for me.   Click Applications>Sound & Video>Tuxguitar...nothing happens....

In terminal i type  "tuxguitar" and i get

"Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)"

---

### Post by ibuclaw on 2008-06-15
Which version of TuxGuitar do you have?

Have you tried the one from the [TG Site]("http://www.tuxguitar.com.ar/")?

[Ubuntu Packages are on this page.]("http://www.tuxguitar.com.ar/download.html")

[EDIT]
You may have to run "**sudo apt-get install -f**" after installing the downloaded deb file to install some missing dependencies.

Regards
Iain

---

### Post by morbid_bean on 2008-06-15
Ok i got it working.... I just had an  unsupported version of java installed for tuxguitar.......thanks for the help

---

