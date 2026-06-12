---
title: "Azureus won't start/load after Gutsy upgrade."
date: 2007-11-01
forum: General Help
---

### Post by dvdadog on 2007-11-01
Hello, after upgrading to Gutsy I can't get Azureus to start.  Nothing happens when clicking on the program icon and when trying from terminal, this is the result:

dvdadog@dvdadog-laptop:~$ azureus
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/widgets/Display (Unsupported major.minor version 49.0)
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
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

I unfortunately do not know what that tells me or what to check from here.  I have already tried a complete removal and reinstallation of Azureus.  Thanks in advance for any help, and let me know if other info is needed.

---

### Post by apoth on 2007-11-01
I believe it's that your Java version is older than required. I think that it might be specifically that you're running Java 1.4 but you need 1.5.

I'd search for 'jre' in Synaptic and perhaps install sun-java-6-jre, I think that's probably most appropriate.

Then if it still doesn't work run the following:

```
sudo update-alternatives --config java
```

Choose the option for the jre you've just installed (should have java-6 in its name somewhere).

---

### Post by dvdadog on 2007-11-01
Thanks, after following your advice it started but would quit right away.  After following the directions from [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/123591](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/123591) it now works.  Thank you for your help I greatly appreciate it.

---

