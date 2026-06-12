---
title: "IPBlock help"
date: 2008-04-03
forum: General Help
---

### Post by manizzle on 2008-04-03
i install iplist. running feisty. click on the icon, and nothing comes up

i do this command to get the gui up

```
sudo ipblock -g
```

and come up with this error

```
Exception in thread "main" java.lang.NoClassDefFoundError: org.ipblock.gui.ipblockUI
   at java.lang.Class.initializeClass(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: java.lang.ProcessBuilder not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/ipblockUI.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)

```

help?..thanks

---

### Post by kpkeerthi on 2008-04-03
Try using Sun's Java Runtime.
```

sudo apt-get install sun-java6-jdk sun-java6-plugin sun-java6-fonts
sudo update-java-alternatives --set java-6-sun

```

---

