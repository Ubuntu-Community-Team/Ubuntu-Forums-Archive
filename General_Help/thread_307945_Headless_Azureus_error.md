---
title: "Headless Azureus error"
date: 2006-11-27
forum: General Help
---

### Post by _pumba_ on 2006-11-27
I am trying to set up a headless Azureus on my Ubuntu 6.10 box.

I have been following this guide [http://azureus.aelitis.com/wiki/index.php/ConsoleUI](http://azureus.aelitis.com/wiki/index.php/ConsoleUI)

And it doesn't start in CLI mode:

```

%>java -jar Azureus2.jar --ui=console

Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.ui.common.Main
   at java.lang.Class.initializeClass(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: org.apache.log4j.Layout not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:Azureus2.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)

```

BTW, I must mention that Azureus works fine in GUI mode.

Does anybody know what's missing and how to fix it?

Thanks

---

