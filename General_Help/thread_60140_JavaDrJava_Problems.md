---
title: "Java/DrJava Problems"
date: 2005-08-26
forum: General Help
---

### Post by zacman on 2005-08-26
I need to use DrJava for a CS class and can't get it to run on Ubuntu.  I downloaded the .jar file but when i run it with java -jar i get a bunch of errors.  I'm probably missing a package but I have no idea what.  Here's the begining of the error output:

java -jar /home/zacman/Desktop/drjava-stable-20050814-2234.jar
java.lang.NoClassDefFoundError: while resolving class: net.java.plaf.windows.common.WindowsTitledBorderPatch
java.lang.NoClassDefFoundError: while resolving class: net.java.plaf.windows.common.WindowsTitledBorderPatch
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at net.java.plaf.LookAndFeelPatchManager.initialize() (Unknown Source)
   at edu.rice.cs.drjava.DrJava.createAndShowGUI(java.lang.String[]) (Unknown Source)
   at edu.rice.cs.drjava.DrJava.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: com.sun.java.swing.plaf.windows.DesktopProperty not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/zacman/Desktop/drjava-stable-20050814-2234.jar], parent=gnu.gcj.runtime.VMClassLoader{urls=[core:/], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   ...9 more
error thrown
Unexpected Window Exception: java.lang.NoClassDefFoundError: while resolving class: net.java.plaf.windows.common.WindowsTitledBorderPatch

....etc. etc. etc.

Anyone know what I need?

---

