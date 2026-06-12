---
title: "azureus won't start"
date: 2007-03-11
forum: General Help
---

### Post by jfenwick on 2007-03-11
Hi there,

I'm using Edgy Eft and Azureus won't start.

When I run it from the terminal this is the error I get:

```
DEBUG::Sun Mar 11 22:49:17 EST 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Sun Mar 11 22:49:17 EST 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
Exception in thread "main" java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:80)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

```

---

### Post by moffa on 2007-03-11
The repository of Azureus is probably borken. Download the latest jar from [http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download]("http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.4.jar?download")

and save it as:

/usr/share/java/Azureus2.jar

---

### Post by jfenwick on 2007-03-12
Oh ya, by the way, I'm on an AMD64.

I downloaded the x86_64 version o fthe jar and copied it over and this is the error I received when trying to start azureus:

```
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.ui.swt.Main
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.ui.swt.Main not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/Azureus2.jar,file:/usr/share/java/bcprov.jar,file:/usr/share/java/log4j-1.2.jar,file:/usr/share/java/commons-cli.jar,file:/usr/lib/java/swt3.2-gtk.jar,file:/usr/share/java/glib0.4.jar,file:/usr/share/java/cairo1.0.jar,file:/usr/share/java/gtk2.10.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

```

---

### Post by moffa on 2007-03-13
Do you have Java installed?  Try typing ```
 java -version 
``` to see what version of java you are running.  If you don't have it installed ```
 sudo apt-get install sun-java5-jre 
```

---

### Post by jfenwick on 2007-03-15
It says I have gcj installed:

```
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by jfenwick on 2007-03-15
I figured it out, I look at the azureus script that you use to start the program, looked at all the libraries, checked each library, and eventually found out that the Azureus2.jar file was corrupted and wouldn't extract or list the files.

---

