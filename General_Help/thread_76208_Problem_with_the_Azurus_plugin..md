---
title: "Problem with the Azurus plugin."
date: 2005-10-14
forum: General Help
---

### Post by dpkg on 2005-10-14
when i start run the program some window for the left of the desktop write:


> 
java.lang.ClassNotFoundException: org.gudy.azureus2.update.UpdaterPatcher
	at java.net.URLClassLoader$1.run(URLClassLoader.java:199)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:684)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:403)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:322)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:156)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run(Initializer.java:270)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport(SWTThread.java:107)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at java.lang.Thread.run(Thread.java:534)


---

