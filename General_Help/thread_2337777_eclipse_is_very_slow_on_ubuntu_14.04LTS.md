---
title: "eclipse is very slow on ubuntu 14.04LTS"
date: 2016-09-21
forum: General Help
---

### Post by esolve3 on 2016-09-21
when I open the eclipse, it is very slow
when I want to open some java files or run some java programs on the eclipse, it is very slow, and sometimes, it become gray/freezed
what can I do to make it run fast?

my Eclipse version:

```

Eclipse Java EE IDE for Web Developers.
Version: Mars.1 Release (4.5.1)

```

eclipse.ini file:

```

-startup
plugins/org.eclipse.equinox.launcher_1.3.100.v20150511-1540.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.300.v20150602-1417
-product
org.eclipse.epp.package.jee.product
--launcher.defaultAction
openFile
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
--launcher.defaultAction
openFile
--launcher.appendVmargs
-vmargs
-Dosgi.requiredJavaVersion=1.7
-XX:MaxPermSize=256m
-Xms256m
-Xmx1024m



```

---

### Post by TheFu on 2016-09-21
Java is a hog.
Eclipse is the largest hog program that I know - worse than Outlook + iTunes together.

The only people I know who are happy with Eclipse have Core i7 desktops with 16G or more of RAM and huge SSDs.

If you have a Core i3 or lesser CPU and less than 8G of RAM, there is next to nothing you can do to make eclipse faster.

---

