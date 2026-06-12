---
title: "cannot get .jpnl to run"
date: 2008-04-29
forum: General Help
---

### Post by 999alfred on 2008-04-29
I am trying to install a satellite tracking app call Satscape and it comes as a jpnl file. I tried using firefox but no lock. I then sabed it and executed with java and this was the result

$ java Satscape.jnlp
Exception in thread "main" java.lang.NoClassDefFoundError: Satscape.jnlp
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: Satscape.jnlp not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)
$

Anybody got an answer?

tj

---

