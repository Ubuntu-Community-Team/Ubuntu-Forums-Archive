---
title: "Can't launch Eclipse after installing"
date: 2020-09-22
forum: General Help
---

### Post by py-ohayo on 2020-09-22
Hello,

Eclipse doesn't run. Here is log:

```
pavel@ALABAMA:~/.eclipse/org.eclipse.platform_3.8_155965261/configuration$ more 1600783043884.log
!SESSION Tue Sep 22 15:57:23 CEST 2020 -----------------------------------------
!ENTRY org.eclipse.equinox.launcher 4 0 2020-09-22 15:57:23.902
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.ClassNotFoundException: org.eclipse.core.runtime.adaptor.EclipseStarter
	at java.base/java.net.URLClassLoader.findClass(URLClassLoader.java:471)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:589)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:626)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
```

Where is a problem ?

Thanks.

---

### Post by howefield on 2020-09-22
Thread moved to the "*General Help*" forum.

---

### Post by py-ohayo on 2020-09-23
Resolved.
I've met this issue following Ubuntu suggestion on **eclipse** install: [FONT=courier new]sudo apt install eclipse-platform[/FONT]
As this didn't work, I uninstalled this version of eclipse.
Then I downloaded installer from here: [https://www.eclipse.org/downloads/packages/](https://www.eclipse.org/downloads/packages/)
and after installing it, **eclipse** launches without problems.

---

### Post by py-ohayo on 2020-09-23
Well ... I was a little quick to say that everything is in order.
Probably I was mistaken when installing. The eclipse is installed in /root/eclipse/cpp-2020-09/ folder.
When I try to launch it "normally", Ubuntu tells that *Command 'eclipse' not found*.
So for lunch it, I have to change to root account, go to the /root/eclipse/cpp-2020-09/ and launch eclipse from there.
Does exist a workaround allowing to launch eclipse from user account and from my home folder.
Thanks.

---

### Post by Impavidus on 2020-09-23
/root is the home directory of the root user. Stuff installed there is typically only available to the root user. Typically nothing is installed there. The normal places to install stuff manually are your own home directory (if you are the only one who will use it), /usr/local (for system-wide installation) or /opt. How you install in those places depends a bit on how the software was packaged.

I don't know why the eclipse you installed from the repos doesn't work. I do know that applications like eclipse should never be run as root.

---

### Post by py-ohayo on 2020-09-24
root was default location when I launch installation and I forgot modify it.
Does exist a simple workaround, or should I reinstall eclipse ?

---

