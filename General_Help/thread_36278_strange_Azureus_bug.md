---
title: "strange Azureus bug"
date: 2005-05-22
forum: General Help
---

### Post by NeoChaosX on 2005-05-22
Okay, I just installed the Azureus 2.3.0.0 backport. However, when I start the program up, I get this strange pop-up telling me about an error loading the plugin 'azupdater'. WHen I click the details button for this, I get this output:

```
java.lang.ClassNotFoundException: org.gudy.azureus2.update.UpdaterPatcher
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native   Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown   Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitiali  zer.loadPluginFromDir(PluginInitializer.java:683)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitiali  zer.loadPluginsFromDir(PluginInitializer.java:402)  
	at org.gudy.azureus2.pluginsimpl.local.PluginInitiali  zer.loadPlugins(PluginInitializer.java:321)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.star  t(AzureusCoreImpl.java:156)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.ru  n(Initializer.java:270)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.ru  nSupport(SWTThread.java:107)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunn  able.java:3:cool:
	at java.lang.Thread.run(Unknown Source)
```
Does anyone know what's going on here?

---

### Post by ow50 on 2005-05-22
Doesn't it pop-up another dialog about how it wants to auto-update the azupdater plugin? Azureus checks, at least by default, for updates to plugins on each startup and offers to install any outdated plugins. Also if it fails to load the azupdater plugin, it should also offer to download it.

---

