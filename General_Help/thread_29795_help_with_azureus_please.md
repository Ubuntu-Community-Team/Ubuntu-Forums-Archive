---
title: "help with azureus please"
date: 2005-04-25
forum: General Help
---

### Post by BiGx5MurF on 2005-04-25
I installed azureus, but when the install finished azureus hung at the splash screen, and this is what it said in the terminal

bigx5murf@Fubar:~$ cd azureus
bigx5murf@Fubar:~/azureus$ ./azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/bigx5murf/azureus/Azureus2.jar:/home/bigx5murf/ azureus/swt.jar:/home/bigx5murf/azureus/swt-mozilla.jar:/home/bigx5murf/azureus/ swt-pi.jar" -Djava.library.path="/home/bigx5murf/azureus" -Dazureus.install.path ="/home/bigx5murf/azureus" org.gudy.azureus2.ui.swt.Main ''
Warning: -Xms16m not understood. Ignoring.
Warning: -Xmx128m not understood. Ignoring.
DEBUG::Mon Apr 25 22:28:48 EDT 2005
  java.lang.ClassNotFoundException: com.sun.net.ssl.internal.ssl.Provider not fo und in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/bigx5murf/azureus/Azur eus2.jar], parent=gnu.gcj.runtime.VMClassLoader{urls=[core:/], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6. 0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgc j.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() ( Unknown Source)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown S ource)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperti es() (Unknown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unk nown Source)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Un known Source)
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknow n Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown S ource)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source)
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source)
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Mon Apr 25 22:28:52 EDT 2005
  java.lang.NoClassDefFoundError: while resolving class: org.gudy.azureus2.ui.swt.auth.AuthenticatorWindow
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run() (Unknown Source)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AERunnable.run() (Unknown Source)
   at java.lang.Thread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: sun.misc.BASE64Encoder not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/bigx5murf/azureus/Azureus2.jar], parent=gnu.gcj.runtime.VMClassLoader{urls=[core:/], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   ...6 more

---

### Post by zjeflegrande on 2005-04-26
Azureus is working for me.

I downloaded Java version 1.5.0_02 from Sun website.
Unpacked this under /usr/share/java
Then edited the azureus-script with the proper paths.

---

