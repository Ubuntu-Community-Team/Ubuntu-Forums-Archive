---
title: "Azureus Troubles"
date: 2008-01-04
forum: General Help
---

### Post by ChrisC098 on 2008-01-04
Ok so ive been using Azureus for the past few days and it's been working fine. Today I woke up and Ubuntu was having trouble connecting to my wireless internet so I restarted and afterwards azureus would not come up. This is what the terminal reads out when I try to boot it from there.

chris@chris-laptop:~$ azureus
DEBUG::Fri Jan 04 14:02:54 GMT-05:00 2008:: org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::152:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::212,ConfigurationManager::initialise::150,ConfigurationManager::getInstance::83,LoggerImpl::init::88,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::72,Main::<init>::56,Main::main::203
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.core3.internat.MessageText
   at java.lang.Class.initializeClass(libgcj.so.81)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:156)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:100)
   at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:76)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:203)

---

### Post by markharding557 on 2008-01-04
have you reinstalled azureus,something could be corrupted and there are alot of references to java check that is  still working properly

---

### Post by ChrisC098 on 2008-01-05
Ok here is what i get after an uninstall/reinstall

chris@chris-laptop:~$ azureus
DEBUG::Sat Jan 05 02:04:02 GMT-05:00 2008:: org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (US). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (US)' (en_US), using 'English (default)'
DEBUG::Sat Jan 05 02:04:04 GMT-05:00 2008:: org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
DEBUG::Sat Jan 05 02:04:05 GMT-05:00 2008:: org.gudy.azureus2.pluginsimpl.local.PluginInitializer::loadPluginFromDir::881:
  java.lang.ClassNotFoundException: com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/Azureus2.jar,file:/usr/share/java/bcprov.jar,file:/usr/share/java/log4j-1.2.jar,file:/usr/share/java/commons-cli.jar,file:/usr/lib/java/swt3.2-gtk.jar,file:/usr/share/java/glib0.4.jar,file:/usr/share/java/cairo1.0.jar,file:/usr/share/java/gtk2.10.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:820)
   at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:510)
   at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:318)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java: 313)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run(Initializer.java: 311)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport(SWTThread.java:115)
   at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
   at java.lang.Thread.run(libgcj.so.81)

Error loading plugin 'azemp' / 'com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin' : java.lang.ClassNotFoundException: com.azureus.plugins.azemp.EmbeddedMediaPlayerPlugin not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/Azureus2.jar,file:/usr/share/java/bcprov.jar,file:/usr/share/java/log4j-1.2.jar,file:/usr/share/java/commons-cli.jar,file:/usr/lib/java/swt3.2-gtk.jar,file:/usr/share/java/glib0.4.jar,file:/usr/share/java/cairo1.0.jar,file:/usr/share/java/gtk2.10.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
[Sat Jan 05 02:04:08 GMT-05:00 2008] Connection write error [version.aelitis.com/81.19.18.34] [<>]: Connection refused
java.io.IOException: message send attempt failed
   at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage(AEClientService.java:169)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:238)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:103)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getExternalIpAddress(VersionCheckClient.java:138)
   at com.aelitis.azureus.core.instancemanager.impl.AZMyInstanceImpl.readExternalAddress(AZMyInstanceImpl.java:207)
   at com.aelitis.azureus.core.instancemanager.impl.AZMyInstanceImpl.getExternalAddress(AZMyInstanceImpl.java:336)
   at com.aelitis.azureus.core.instancemanager.impl.AZInstanceImpl.encode(AZInstanceImpl.java:47)
   at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.sendMessage(AZInstanceManagerImpl.java:348)
   at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.sendMessage(AZInstanceManagerImpl.java:330)
   at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl$request.<init>(AZInstanceManagerImpl.java:1213)
   at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.sendRequest(AZInstanceManagerImpl.java:1172)
   at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.search(AZInstanceManagerImpl.java:661)
   at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl$4.runSupport(AZInstanceManagerImpl.java:241)
   at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Aborted (core dumped)

---

