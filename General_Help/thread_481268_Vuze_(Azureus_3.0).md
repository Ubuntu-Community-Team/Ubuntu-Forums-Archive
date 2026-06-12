---
title: "Vuze (Azureus 3.0)"
date: 2007-06-22
forum: General Help
---

### Post by BrokeBody on 2007-06-22
I downloaded .jar file and tried this:

```

java -jar Azureus3.0.1.6.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.ui.common.Main
   at java.lang.Class.initializeClass(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.CommandLineParser not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:Azureus3.0.1.6.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)

```

Now what? How do I install it?

---

### Post by pldg on 2007-09-10
You need Sun's Java installed, preferably >=1.6.0, but at least on my machine aptitude didn't include this instance in /etc/jvm after its installation, so please check that /usr/lib/jvm/java-6-sun is on top of the file (higher priority).

I also had other issues trying to run the standalone version (not apt), such as the directory to run azureus from. I installed it in /usr/local/azureus and created a link as /usr/bin/azureus -> /usr/share/azureus/azureus, but this wouldn't work as an icon under gnome (poor environment settings, I believe). In the end, I resorted to modifying the icon properties to suit the exact location of the executable script, i.e. /usr/local/azureus/azureus.

---

### Post by Perfect Storm on 2007-09-10
Here's a guide: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

---

