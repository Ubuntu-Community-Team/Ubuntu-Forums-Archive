---
title: "Error when reinstalling eclipse..."
date: 2007-08-21
forum: General Help
---

### Post by J4DED on 2007-08-21
When I uninstalled and the reinstalled eclipse - I received the following error:

> An error has occurred. See the log file
/home/atom/.eclipse/org.eclipse.platform_3.2.0/configuration/1187712738064.log.

How do I resolve this?

When I open the log file it contains:
> !SESSION 2007-08-21 12:12:17.852 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_CA
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-08-21 12:12:26.001
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-21 12:12:26.001
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-21 12:12:26.002
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-21 12:12:26.002
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-08-21 12:12:26.094
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (92).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   ...58 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...61 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...61 more

!ENTRY org.eclipse.osgi 4 0 2007-08-21 12:12:26.289
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (236).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   ...29 more
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-08-21 12:12:26.302
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.throwException(RegistryStrategyOSGI.java:165)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:149)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.user.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.user.nl2 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.jdt.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors.nl1 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.ui.editors_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.text.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.text.nl2 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui.nl2 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui.nlBidi 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.team.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.ide.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.nlBidi 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.ui.ide_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.nl2 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.platform_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.ide.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.nl2 2 0 2007-08-21 12:12:26.774
!MESSAGE Missing host org.eclipse.ui.ide_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.774
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.doc.user.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.doc.user.nl2 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.pde.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.ide.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.nl1 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.ui.ide_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.core.refactoring.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.core.refactoring.nl2 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.ltk.core.refactoring_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.nl1 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.ui.views_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nl1 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.source.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.source.nl1 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.jdt.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.user.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.user.nlBidi 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.jdt.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui.nlBidi 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.team.cvs.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.compare.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.compare.nlBidi 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.compare_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.browser.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser.nl1 2 0 2007-08-21 12:12:26.775
!MESSAGE Missing host org.eclipse.ui.browser_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.775
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.base.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.base.nl1 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.help.base_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring.nl1 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.ltk.ui.refactoring_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.webapp.nl[/email]1_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.help.webapp.nl1 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.help.webapp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.junit.runtime.nlBi[/email]di_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.junit.runtime.nlBidi 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.core.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.debug.core.nl2 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.debug.core_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.text.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.text.nlBidi 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.resources.nl2 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.core.resources_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nl2 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.core.nlBidi 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.team.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.776
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.core.nl2 2 0 2007-08-21 12:12:26.776
!MESSAGE Missing host org.eclipse.update.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.777
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.nl2 2 0 2007-08-21 12:12:26.777
!MESSAGE Missing host org.eclipse.ui.views_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.777
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui.nl1 2 0 2007-08-21 12:12:26.777
!MESSAGE Missing host org.eclipse.update.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.777
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.base.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.base.nl2 2 0 2007-08-21 12:12:26.777
!MESSAGE Missing host org.eclipse.help.base_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.777
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jface.nl1 2 0 2007-08-21 12:12:26.777
!MESSAGE Missing host org.eclipse.jface_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.777
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.nlBidi 2 0 2007-08-21 12:12:26.777
!MESSAGE Missing host org.eclipse.jdt.junit_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.777
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.nl2 2 0 2007-08-21 12:12:26.777
!MESSAGE Missing host org.eclipse.ui.workbench_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nl2 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.ant.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ant.ui.nlBidi 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.ant.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime.nlBidi 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.core.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.browser.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser.nlBidi 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.ui.browser_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.ui.nl2 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.jdt.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui.nlBidi 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nl1 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.nl2 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.jdt.junit_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.cheatsheets.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets.nlBidi 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.ui.cheatsheets_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.778
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.nlBidi 2 0 2007-08-21 12:12:26.778
!MESSAGE Missing host org.eclipse.jdt.debug_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.scheduler.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler.nlBidi 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.update.scheduler_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.core.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.core.nl1 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.pde.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui.nl2 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.team.cvs.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nl1 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui.nl2 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.team.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.core.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.core.nl1 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.team.cvs.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.text.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text.nl2 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.jface.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.nl1 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.nl1 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.ui.workbench_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.779
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nl2 2 0 2007-08-21 12:12:26.779
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.780
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.isv.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.isv.nl2 2 0 2007-08-21 12:12:26.780
!MESSAGE Missing host org.eclipse.jdt.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.780
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.scheduler.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler.nl2 2 0 2007-08-21 12:12:26.780
!MESSAGE Missing host org.eclipse.update.scheduler_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.780
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.cheatsheets.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets.nl2 2 0 2007-08-21 12:12:26.780
!MESSAGE Missing host org.eclipse.ui.cheatsheets_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.780
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.core.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.core.nl2 2 0 2007-08-21 12:12:26.780
!MESSAGE Missing host org.eclipse.pde.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.780
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.nl2 2 0 2007-08-21 12:12:26.780
!MESSAGE Missing host org.eclipse.jdt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.780
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.text.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text.nl1 2 0 2007-08-21 12:12:26.780
!MESSAGE Missing host org.eclipse.jface.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.780
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]1_4.1.30.1/ was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nl1 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui.nl2 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.update.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.scheduler.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler.nl1 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.update.scheduler_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime.nl1 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.core.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui.nl1 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.team.cvs.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.nlBidi 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.help_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.core.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.core.nlBidi 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.pde.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.compare.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.compare.nl2 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.compare_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nlBidi 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.781
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jface.nlBidi 2 0 2007-08-21 12:12:26.781
!MESSAGE Missing host org.eclipse.jface_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.782
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.nl2 2 0 2007-08-21 12:12:26.782
!MESSAGE Missing host org.eclipse.jdt.debug_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.782
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.resources.nl1 2 0 2007-08-21 12:12:26.782
!MESSAGE Missing host org.eclipse.core.resources_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.782
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nl2 2 0 2007-08-21 12:12:26.782
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.782
!MESSAGE Bundle [email]update@plugins/org.eclipse.search.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.search.nlBidi 2 0 2007-08-21 12:12:26.782
!MESSAGE Missing host org.eclipse.search_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.782
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.presentations.r21.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21.nlBidi 2 0 2007-08-21 12:12:26.783
!MESSAGE Missing host org.eclipse.ui.presentations.r21_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.783
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.build.nl[/email]2_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.build.nl2 2 0 2007-08-21 12:12:26.783
!MESSAGE Missing host org.eclipse.pde.build_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.783
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.ui.nl2 2 0 2007-08-21 12:12:26.783
!MESSAGE Missing host org.eclipse.jdt.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.783
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.launching.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.launching.nl2 2 0 2007-08-21 12:12:26.783
!MESSAGE Missing host org.eclipse.jdt.launching_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.783
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh.nl1 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.team.cvs.ssh_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.nl2 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.ui.intro_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.nlBidi 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.launching.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.launching.nl1 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.jdt.launching_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nlBidi 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filebuffers.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.filebuffers.nl1 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.core.filebuffers_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.resources.nlBidi 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.core.resources_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.doc.user.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.doc.user.nlBidi 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.pde.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.swt.nl1 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.swt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.source.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.source.nl1 2 0 2007-08-21 12:12:26.784
!MESSAGE Missing host org.eclipse.platform.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.784
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.nlBidi 2 0 2007-08-21 12:12:26.785
!MESSAGE Missing host org.eclipse.jdt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.785
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh.nlBidi 2 0 2007-08-21 12:12:26.785
!MESSAGE Missing host org.eclipse.team.cvs.ssh_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.785
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh2.nl[/email]2_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh2.nl2 2 0 2007-08-21 12:12:26.785
!MESSAGE Missing host org.eclipse.team.cvs.ssh2_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.785
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.isv.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.isv.nlBidi 2 0 2007-08-21 12:12:26.785
!MESSAGE Missing host org.eclipse.platform.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.785
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.base.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.base.nlBidi 2 0 2007-08-21 12:12:26.785
!MESSAGE Missing host org.eclipse.help.base_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.785
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.webapp.nl[/email]2_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.help.webapp.nl2 2 0 2007-08-21 12:12:26.785
!MESSAGE Missing host org.eclipse.help.webapp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.785
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.commands.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.commands.nl1 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.core.commands_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.user.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.user.nl2 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.platform.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.runtime.nl[/email]1_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.runtime.nl1 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.jdt.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.runtime.nl[/email]2_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.runtime.nl2 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.jdt.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.ui.nlBidi 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.jdt.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.nl2 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.help_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.isv.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.isv.nl1 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.jdt.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.webapp.nlBi[/email]di_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.help.webapp.nlBidi 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.help.webapp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nlBidi 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.runtime.nlBi[/email]di_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.runtime.nlBidi 2 0 2007-08-21 12:12:26.786
!MESSAGE Missing host org.eclipse.jdt.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.786
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.build.nl[/email]1_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.build.nl1 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.pde.build_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors.nl2 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.ui.editors_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh2.nl[/email]1_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh2.nl1 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.team.cvs.ssh2_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.user.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.user.nl1 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.jdt.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]2_4.1.30.1/ was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nl2 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nlBidi 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.presentations.r21.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21.nl1 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.ui.presentations.r21_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.expressions.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.expressions.nl2 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.core.expressions_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.nl1 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.platform_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.texteditor.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor.nl2 2 0 2007-08-21 12:12:26.787
!MESSAGE Missing host org.eclipse.ui.workbench.texteditor_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.787
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.nlBidi 2 0 2007-08-21 12:12:26.788
!MESSAGE Missing host org.eclipse.ui.views_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.788
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nlBi[/email]di_4.1.30.1/ was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nlBidi 2 0 2007-08-21 12:12:26.788
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.788
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nlBidi 2 0 2007-08-21 12:12:26.788
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.788
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.commands.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.commands.nlBidi 2 0 2007-08-21 12:12:26.788
!MESSAGE Missing host org.eclipse.core.commands_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.788
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.core.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.core.nlBidi 2 0 2007-08-21 12:12:26.788
!MESSAGE Missing host org.eclipse.jdt.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.788
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.isv.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.isv.nl2 2 0 2007-08-21 12:12:26.788
!MESSAGE Missing host org.eclipse.platform.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.788
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh.nl2 2 0 2007-08-21 12:12:26.788
!MESSAGE Missing host org.eclipse.team.cvs.ssh_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.nl1 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.jdt.debug_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.ui.nl1 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.jdt.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.core.nlBidi 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.update.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.nlBidi 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.ui.workbench_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.nl1 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.jdt.junit_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.text.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.text.nl1 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.doc.user.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.doc.user.nl1 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.pde.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.forms.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms.nl1 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.ui.forms_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.nlBidi 2 0 2007-08-21 12:12:26.789
!MESSAGE Missing host org.eclipse.ui.intro_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.789
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.nl1 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.jdt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.user.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.user.nl1 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.platform.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.presentations.r21.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21.nl2 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.ui.presentations.r21_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui.nl2 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.help.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.configurator.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator.nlBidi 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.update.configurator_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.junit.runtime.nl[/email]2_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.junit.runtime.nl2 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nl1 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nl1 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.swt.nlBidi 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.swt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui.nlBidi 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.help.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.790
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.text.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text.nlBidi 2 0 2007-08-21 12:12:26.790
!MESSAGE Missing host org.eclipse.jface.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.core.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.debug.core.nl1 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.debug.core_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime.nl2 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.core.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui.nl1 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.ant.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ant.ui.nl2 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.ant.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui.nl1 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.team.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.core.nl1 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.update.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.source.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.source.nlBidi 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.jdt.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.ui.nl1 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.jdt.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.nl1 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.help_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.791
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filebuffers.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.filebuffers.nl2 2 0 2007-08-21 12:12:26.791
!MESSAGE Missing host org.eclipse.core.filebuffers_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.792
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.texteditor.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor.nlBidi 2 0 2007-08-21 12:12:26.792
!MESSAGE Missing host org.eclipse.ui.workbench.texteditor_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.792
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.core.nl2 2 0 2007-08-21 12:12:26.792
!MESSAGE Missing host org.eclipse.team.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.792
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.core.refactoring.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.core.refactoring.nlBidi 2 0 2007-08-21 12:12:26.792
!MESSAGE Missing host org.eclipse.ltk.core.refactoring_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.792
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filebuffers.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.filebuffers.nlBidi 2 0 2007-08-21 12:12:26.792
!MESSAGE Missing host org.eclipse.core.filebuffers_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.792
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nl2 2 0 2007-08-21 12:12:26.792
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.792
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.browser.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser.nl2 2 0 2007-08-21 12:12:26.792
!MESSAGE Missing host org.eclipse.ui.browser_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.nl1 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.ui.intro_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nl1 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.core.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.debug.core.nlBidi 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.debug.core_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.user.nlBi[/email]di/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.user.nlBidi 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.platform.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.source.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.source.nl2 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.jdt.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.configurator.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator.nl1 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.update.configurator_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.launching.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.launching.nlBidi 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.jdt.launching_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.build.nlBi[/email]di_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.build.nlBidi 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.pde.build_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.core.refactoring.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.core.refactoring.nl1 2 0 2007-08-21 12:12:26.793
!MESSAGE Missing host org.eclipse.ltk.core.refactoring_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.793
!MESSAGE Bundle [email]update@plugins/org.eclipse.search.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.search.nl1 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.search_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.forms.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms.nl2 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.ui.forms_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.configurator.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator.nl2 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.update.configurator_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.isv.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.isv.nlBidi 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.jdt.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.texteditor.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor.nl1 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.ui.workbench.texteditor_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.expressions.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.expressions.nlBidi 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.core.expressions_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors.nlBidi 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.ui.editors_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.junit.runtime.nl[/email]1_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.junit.runtime.nl1 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.isv.nl[/email]1_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.isv.nl1 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.platform.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.ant.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ant.ui.nl1 2 0 2007-08-21 12:12:26.794
!MESSAGE Missing host org.eclipse.ant.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.794
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.core.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.core.nlBidi 2 0 2007-08-21 12:12:26.795
!MESSAGE Missing host org.eclipse.team.cvs.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.795
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh2.nlBi[/email]di_3.1.0/ was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh2.nlBidi 2 0 2007-08-21 12:12:26.795
!MESSAGE Missing host org.eclipse.team.cvs.ssh2_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.795
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring.nlBidi 2 0 2007-08-21 12:12:26.795
!MESSAGE Missing host org.eclipse.ltk.ui.refactoring_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.795
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring.nl2 2 0 2007-08-21 12:12:26.795
!MESSAGE Missing host org.eclipse.ltk.ui.refactoring_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.795
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jface.nl2 2 0 2007-08-21 12:12:26.795
!MESSAGE Missing host org.eclipse.jface_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.795
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.commands.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.commands.nl2 2 0 2007-08-21 12:12:26.795
!MESSAGE Missing host org.eclipse.core.commands_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.795
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.forms.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms.nlBidi 2 0 2007-08-21 12:12:26.795
!MESSAGE Missing host org.eclipse.ui.forms_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.search.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.search.nl2 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.search_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.ui.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui.nl1 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.help.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.core.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.core.nl2 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.team.cvs.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.core.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.core.nl1 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.jdt.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.nl2_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.swt.nl2 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.swt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.source.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.source.nlBidi 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.platform.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.team.core.nl1 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.team.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.nl2 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.ui.nlBidi 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.jdt.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.796
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.nlBi[/email]di_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.nlBidi 2 0 2007-08-21 12:12:26.796
!MESSAGE Missing host org.eclipse.platform_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.source.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.platform.source.nl2 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.platform.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nl[/email]2_3.1.1/ was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nl2 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.compare.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.compare.nl1 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.compare_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.cheatsheets.nl1_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets.nl1 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.ui.cheatsheets_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.core.nl2_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.core.nl2 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.jdt.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.ui.nlBidi_3.1.1.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui.nlBidi 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.update.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nlBidi_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nlBidi 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:26.797
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.expressions.nl1_3.1.0.jar[/email] was not resolved.
!SUBENTRY 2 org.eclipse.core.expressions.nl1 2 0 2007-08-21 12:12:26.797
!MESSAGE Missing host org.eclipse.core.expressions_[3.1.0,3.2.0).

!ENTRY org.eclipse.osgi 2 0 2007-08-21 12:12:27.026
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.026
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.source.nl[/email]1_3.1.1/ [4] was not resolved.
!SUBENTRY 2 org.eclipse.platform.source.nl1 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.platform.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nl[/email]2_3.1.1/ [6] was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nl2 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.nl2_3.1.1.jar[/email] [7] was not resolved.
!SUBENTRY 2 org.eclipse.ui.nl2 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.base.nl1_3.1.0.jar[/email] [8] was not resolved.
!SUBENTRY 2 org.eclipse.help.base.nl1 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.help.base_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.nl1_3.1.1.jar[/email] [9] was not resolved.
!SUBENTRY 2 org.eclipse.ui.nl1 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.ui.nl1_3.1.1.jar[/email] [11] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.ui.nl1 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.jdt.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.core.nlBidi_3.1.0.jar[/email] [12] was not resolved.
!SUBENTRY 2 org.eclipse.debug.core.nlBidi 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.debug.core_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.isv.nl[/email]2_3.1.1/ [16] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.isv.nl2 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.jdt.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.nlBidi_3.1.1.jar[/email] [18] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.nlBidi 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.ui.workbench_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.source.nl[/email]2_3.1.1/ [19] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.source.nl2 2 0 2007-08-21 12:12:27.027
!MESSAGE Missing host org.eclipse.jdt.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.027
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.ui.nlBidi_3.1.1.jar[/email] [20] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.ui.nlBidi 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.jdt.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.scheduler.nl2_3.1.0.jar[/email] [22] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler.nl2 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.update.scheduler_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.isv.nlBi[/email]di_3.1.1/ [23] was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.isv.nlBidi 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.platform.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.launching.nlBidi_3.1.0.jar[/email] [25] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.launching.nlBidi 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.jdt.launching_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core.nlBidi_3.1.1.jar[/email] [27] was not resolved.
!SUBENTRY 2 org.eclipse.team.core.nlBidi 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.team.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.nl2_3.1.0.jar[/email] [28] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.nl2 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.jdt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core.nl2_3.1.1.jar[/email] [33] was not resolved.
!SUBENTRY 2 org.eclipse.update.core.nl2 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.update.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]1_4.1.30.1/ [34] was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nl1 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.commands.nl1_3.1.0.jar[/email] [35] was not resolved.
!SUBENTRY 2 org.eclipse.core.commands.nl1 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.core.commands_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views.nl2_3.1.1.jar[/email] [39] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.nl2 2 0 2007-08-21 12:12:27.028
!MESSAGE Missing host org.eclipse.ui.views_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.028
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.scheduler.nl1_3.1.0.jar[/email] [40] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler.nl1 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.update.scheduler_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.user.nl[/email]2_3.1.1/ [41] was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.user.nl2 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.platform.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.cheatsheets.nlBidi_3.1.1.jar[/email] [46] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets.nlBidi 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.ui.cheatsheets_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.launching.nl1_3.1.0.jar[/email] [47] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.launching.nl1 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.jdt.launching_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views.nlBidi_3.1.1.jar[/email] [48] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.nlBidi 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.ui.views_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core.nl1_3.1.1.jar[/email] [49] was not resolved.
!SUBENTRY 2 org.eclipse.update.core.nl1 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.update.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.core.refactoring.nl2_3.1.0.jar[/email] [51] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.core.refactoring.nl2 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.ltk.core.refactoring_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.nlBi[/email]di_3.1.1/ [52] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.nlBidi 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.jdt.debug_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.029
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nlBidi_3.1.1.jar[/email] [53] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nlBidi 2 0 2007-08-21 12:12:27.029
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nlBi[/email]di_4.1.30.1/ [54] was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nlBidi 2 0 2007-08-21 12:12:27.030
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.source.nlBi[/email]di_3.1.1/ [55] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.source.nlBidi 2 0 2007-08-21 12:12:27.030
!MESSAGE Missing host org.eclipse.jdt.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views.nl1_3.1.1.jar[/email] [57] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.nl1 2 0 2007-08-21 12:12:27.030
!MESSAGE Missing host org.eclipse.ui.views_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filebuffers.nl1_3.1.0.jar[/email] [59] was not resolved.
!SUBENTRY 2 org.eclipse.core.filebuffers.nl1 2 0 2007-08-21 12:12:27.030
!MESSAGE Missing host org.eclipse.core.filebuffers_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nlBi[/email]di_3.1.1/ [60] was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nlBidi 2 0 2007-08-21 12:12:27.030
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.ui.nl1_3.1.1.jar[/email] [61] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.ui.nl1 2 0 2007-08-21 12:12:27.030
!MESSAGE Missing host org.eclipse.jdt.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nl1_3.1.0.jar[/email] [63] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nl1 2 0 2007-08-21 12:12:27.030
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.030
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.scheduler.nlBidi_3.1.0.jar[/email] [64] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler.nlBidi 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.update.scheduler_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.nl1_3.1.0.jar[/email] [67] was not resolved.
!SUBENTRY 2 org.eclipse.help.nl1 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.help_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.source.nl[/email]1_3.1.1/ [69] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.source.nl1 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.jdt.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.core.nl1_3.1.1.jar[/email] [70] was not resolved.
!SUBENTRY 2 org.eclipse.pde.core.nl1 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.pde.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.commands.nlBidi_3.1.0.jar[/email] [72] was not resolved.
!SUBENTRY 2 org.eclipse.core.commands.nlBidi 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.core.commands_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filebuffers.nl2_3.1.0.jar[/email] [73] was not resolved.
!SUBENTRY 2 org.eclipse.core.filebuffers.nl2 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.core.filebuffers_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.nl2_3.1.0.jar[/email] [74] was not resolved.
!SUBENTRY 2 org.eclipse.swt.nl2 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.swt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ui.nl2_3.1.1.jar[/email] [76] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui.nl2 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.team.cvs.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.core.nlBidi_3.1.1.jar[/email] [78] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.core.nlBidi 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.jdt.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.texteditor.nlBidi_3.1.1.jar[/email] [79] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor.nlBidi 2 0 2007-08-21 12:12:27.031
!MESSAGE Missing host org.eclipse.ui.workbench.texteditor_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.031
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ui.nlBidi_3.1.1.jar[/email] [81] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui.nlBidi 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.team.cvs.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources.nlBidi_3.1.0.jar[/email] [83] was not resolved.
!SUBENTRY 2 org.eclipse.core.resources.nlBidi 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.core.resources_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh.nl2_3.1.0.jar[/email] [84] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh.nl2 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.team.cvs.ssh_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.core.refactoring.nlBidi_3.1.0.jar[/email] [85] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.core.refactoring.nlBidi 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.ltk.core.refactoring_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.browser.nl1_3.1.1.jar[/email] [87] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser.nl1 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.ui.browser_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.text.nl2_3.1.1.jar[/email] [88] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text.nl2 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.jface.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.nl1_3.1.0.jar[/email] [89] was not resolved.
!SUBENTRY 2 org.eclipse.swt.nl1 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.swt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.browser.nl2_3.1.1.jar[/email] [91] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser.nl2 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.ui.browser_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.webapp.nl[/email]1_3.1.0/ [93] was not resolved.
!SUBENTRY 2 org.eclipse.help.webapp.nl1 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.help.webapp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh.nlBidi_3.1.0.jar[/email] [95] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh.nlBidi 2 0 2007-08-21 12:12:27.032
!MESSAGE Missing host org.eclipse.team.cvs.ssh_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.032
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core.nlBidi_3.1.1.jar[/email] [96] was not resolved.
!SUBENTRY 2 org.eclipse.update.core.nlBidi 2 0 2007-08-21 12:12:27.033
!MESSAGE Missing host org.eclipse.update.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.033
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro.nl1_3.1.1.jar[/email] [97] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.nl1 2 0 2007-08-21 12:12:27.033
!MESSAGE Missing host org.eclipse.ui.intro_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.033
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.junit.runtime.nlBi[/email]di_3.1.0/ [99] was not resolved.
!SUBENTRY 2 org.eclipse.pde.junit.runtime.nlBidi 2 0 2007-08-21 12:12:27.033
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.033
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nl2_3.1.1.jar[/email] [100] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nl2 2 0 2007-08-21 12:12:27.033
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.033
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.nl[/email]1_3.1.1/ [102] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.nl1 2 0 2007-08-21 12:12:27.033
!MESSAGE Missing host org.eclipse.jdt.junit_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.033
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources.nl2_3.1.0.jar[/email] [105] was not resolved.
!SUBENTRY 2 org.eclipse.core.resources.nl2 2 0 2007-08-21 12:12:27.033
!MESSAGE Missing host org.eclipse.core.resources_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.033
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.presentations.r21.nl2_3.1.0.jar[/email] [108] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21.nl2 2 0 2007-08-21 12:12:27.033
!MESSAGE Missing host org.eclipse.ui.presentations.r21_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.033
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.nl2_3.1.1.jar[/email] [111] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.nl2 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.ui.workbench_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources.nl1_3.1.0.jar[/email] [112] was not resolved.
!SUBENTRY 2 org.eclipse.core.resources.nl1 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.core.resources_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.isv.nl[/email]1_3.1.1/ [115] was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.isv.nl1 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.platform.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.core.nl2_3.1.1.jar[/email] [116] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.core.nl2 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.jdt.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.ui.nl2_3.1.1.jar[/email] [120] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui.nl2 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.help.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.ui.nlBidi_3.1.1.jar[/email] [122] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui.nlBidi 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.update.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nl2_3.1.0.jar[/email] [123] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nl2 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.configurator.nlBidi_3.1.0.jar[/email] [126] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator.nlBidi 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.update.configurator_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.ant.ui.nl1_3.1.1.jar[/email] [127] was not resolved.
!SUBENTRY 2 org.eclipse.ant.ui.nl1 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.ant.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nlBidi_3.1.0.jar[/email] [128] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nlBidi 2 0 2007-08-21 12:12:27.034
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.034
!MESSAGE Bundle [email]update@plugins/org.eclipse.ant.ui.nlBidi_3.1.1.jar[/email] [129] was not resolved.
!SUBENTRY 2 org.eclipse.ant.ui.nlBidi 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.ant.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.junit.runtime.nl[/email]2_3.1.0/ [132] was not resolved.
!SUBENTRY 2 org.eclipse.pde.junit.runtime.nl2 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.core.nlBidi_3.1.1.jar[/email] [133] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.core.nlBidi 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.team.cvs.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.expressions.nl1_3.1.0.jar[/email] [134] was not resolved.
!SUBENTRY 2 org.eclipse.core.expressions.nl1 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.core.expressions_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nl2_3.1.0.jar[/email] [136] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nl2 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nl[/email]1_3.1.1/ [138] was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nl1 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh2.nlBi[/email]di_3.1.0/ [139] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh2.nlBidi 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.team.cvs.ssh2_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.nlBidi_3.1.1.jar[/email] [141] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime.nlBidi 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.core.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.webapp.nlBi[/email]di_3.1.0/ [143] was not resolved.
!SUBENTRY 2 org.eclipse.help.webapp.nlBidi 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.help.webapp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.035
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp.nl1_3.1.0.jar[/email] [144] was not resolved.
!SUBENTRY 2 org.eclipse.rcp.nl1 2 0 2007-08-21 12:12:27.035
!MESSAGE Missing host org.eclipse.rcp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.036
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.user.nl[/email]2_3.1.1/ [146] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.user.nl2 2 0 2007-08-21 12:12:27.036
!MESSAGE Missing host org.eclipse.jdt.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.036
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nlBidi_3.1.1.jar[/email] [149] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nlBidi 2 0 2007-08-21 12:12:27.036
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.036
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.nlBidi_3.1.0.jar[/email] [150] was not resolved.
!SUBENTRY 2 org.eclipse.swt.nlBidi 2 0 2007-08-21 12:12:27.036
!MESSAGE Missing host org.eclipse.swt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.036
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring.nlBidi_3.1.1.jar[/email] [151] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring.nlBidi 2 0 2007-08-21 12:12:27.036
!MESSAGE Missing host org.eclipse.ltk.ui.refactoring_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.036
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors.nl1_3.1.1.jar[/email] [152] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors.nl1 2 0 2007-08-21 12:12:27.036
!MESSAGE Missing host org.eclipse.ui.editors_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.036
!MESSAGE Bundle [email]update@plugins/org.eclipse.search.nlBidi_3.1.1.jar[/email] [154] was not resolved.
!SUBENTRY 2 org.eclipse.search.nlBidi 2 0 2007-08-21 12:12:27.036
!MESSAGE Missing host org.eclipse.search_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.036
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.runtime.nlBi[/email]di_3.1.0/ [155] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.runtime.nlBidi 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.jdt.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.build.nl[/email]1_3.1.0/ [161] was not resolved.
!SUBENTRY 2 org.eclipse.pde.build.nl1 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.pde.build_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.ui.nlBidi_3.1.1.jar[/email] [162] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui.nlBidi 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.help.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.text.nl2_3.1.1.jar[/email] [164] was not resolved.
!SUBENTRY 2 org.eclipse.text.nl2 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors.nl2_3.1.1.jar[/email] [167] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors.nl2 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.ui.editors_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring.nl2_3.1.1.jar[/email] [169] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring.nl2 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.ltk.ui.refactoring_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.ui.nl2_3.1.1.jar[/email] [170] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui.nl2 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.browser.nlBidi_3.1.1.jar[/email] [171] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser.nlBidi 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.ui.browser_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.presentations.r21.nlBidi_3.1.0.jar[/email] [172] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21.nlBidi 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.ui.presentations.r21_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh2.nl[/email]1_3.1.0/ [173] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh2.nl1 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.team.cvs.ssh2_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.037
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.text.nlBidi_3.1.1.jar[/email] [174] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text.nlBidi 2 0 2007-08-21 12:12:27.037
!MESSAGE Missing host org.eclipse.jface.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui.nlBidi_3.1.1.jar[/email] [176] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui.nlBidi 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.team.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.build.nl[/email]2_3.1.0/ [178] was not resolved.
!SUBENTRY 2 org.eclipse.pde.build.nl2 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.pde.build_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.user.nl[/email]1_3.1.1/ [179] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.user.nl1 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.jdt.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.nl2_3.1.1.jar[/email] [181] was not resolved.
!SUBENTRY 2 org.eclipse.jface.nl2 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.jface_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.ide.nlBidi_3.1.1.jar[/email] [182] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.nlBidi 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.ui.ide_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.ui.nl2_3.1.1.jar[/email] [184] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.ui.nl2 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.jdt.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]2_4.1.30.1/ [185] was not resolved.
!SUBENTRY 2 org.eclipse.tomcat.nl2 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.tomcat_[4.1.30.1,4.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.core.nl1_3.1.0.jar[/email] [186] was not resolved.
!SUBENTRY 2 org.eclipse.debug.core.nl1 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.debug.core_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.sdk.nlBi[/email]di_3.1.1/ [191] was not resolved.
!SUBENTRY 2 org.eclipse.sdk.nlBidi 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.sdk_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.038
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.commands.nl2_3.1.0.jar[/email] [193] was not resolved.
!SUBENTRY 2 org.eclipse.core.commands.nl2 2 0 2007-08-21 12:12:27.038
!MESSAGE Missing host org.eclipse.core.commands_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.nl[/email]2_3.1.1/ [194] was not resolved.
!SUBENTRY 2 org.eclipse.platform.nl2 2 0 2007-08-21 12:12:27.039
!MESSAGE Missing host org.eclipse.platform_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.ui.nl2_3.1.1.jar[/email] [195] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.ui.nl2 2 0 2007-08-21 12:12:27.039
!MESSAGE Missing host org.eclipse.jdt.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.launching.nl2_3.1.0.jar[/email] [196] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.launching.nl2 2 0 2007-08-21 12:12:27.039
!MESSAGE Missing host org.eclipse.jdt.launching_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.nl2_3.1.1.jar[/email] [198] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime.nl2 2 0 2007-08-21 12:12:27.039
!MESSAGE Missing host org.eclipse.core.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.forms.nlBidi_3.1.0.jar[/email] [199] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms.nlBidi 2 0 2007-08-21 12:12:27.039
!MESSAGE Missing host org.eclipse.ui.forms_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.presentations.r21.nl1_3.1.0.jar[/email] [203] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21.nl1 2 0 2007-08-21 12:12:27.039
!MESSAGE Missing host org.eclipse.ui.presentations.r21_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.ui.nl1_3.1.1.jar[/email] [204] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui.nl1 2 0 2007-08-21 12:12:27.039
!MESSAGE Missing host org.eclipse.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.039
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.ide.nl2_3.1.1.jar[/email] [206] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.nl2 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.ui.ide_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh.nl1_3.1.0.jar[/email] [208] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh.nl1 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.team.cvs.ssh_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.expressions.nl2_3.1.0.jar[/email] [209] was not resolved.
!SUBENTRY 2 org.eclipse.core.expressions.nl2 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.core.expressions_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.doc.user.nl[/email]2_3.1.1/ [212] was not resolved.
!SUBENTRY 2 org.eclipse.pde.doc.user.nl2 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.pde.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.ui.nlBidi_3.1.1.jar[/email] [213] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui.nlBidi 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro.nl2_3.1.1.jar[/email] [214] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.nl2 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.ui.intro_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.search.nl2_3.1.1.jar[/email] [217] was not resolved.
!SUBENTRY 2 org.eclipse.search.nl2 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.search_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.ide.nl1_3.1.1.jar[/email] [218] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.nl1 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.ui.ide_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nl1_3.1.1.jar[/email] [219] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nl1 2 0 2007-08-21 12:12:27.040
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.040
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.nl[/email]1_3.1.1/ [221] was not resolved.
!SUBENTRY 2 org.eclipse.platform.nl1 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.platform_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.ant.ui.nl2_3.1.1.jar[/email] [222] was not resolved.
!SUBENTRY 2 org.eclipse.ant.ui.nl2 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.ant.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.ui.nl1_3.1.1.jar[/email] [223] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui.nl1 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.help.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.core.nl2_3.1.1.jar[/email] [229] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.core.nl2 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.team.cvs.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.nl[/email]2_3.1.1/ [231] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.nl2 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.jdt.junit_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.nlBidi_3.1.1.jar[/email] [232] was not resolved.
!SUBENTRY 2 org.eclipse.ui.nlBidi 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.texteditor.nl2_3.1.1.jar[/email] [233] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor.nl2 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.ui.workbench.texteditor_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui.nl1_3.1.1.jar[/email] [234] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui.nl1 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.team.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.webapp.nl[/email]2_3.1.0/ [235] was not resolved.
!SUBENTRY 2 org.eclipse.help.webapp.nl2 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.help.webapp_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.core.refactoring.nl1_3.1.0.jar[/email] [237] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.core.refactoring.nl1 2 0 2007-08-21 12:12:27.041
!MESSAGE Missing host org.eclipse.ltk.core.refactoring_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.041
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.nl1_3.1.1.jar[/email] [240] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime.nl1 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.core.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.search.nl1_3.1.1.jar[/email] [243] was not resolved.
!SUBENTRY 2 org.eclipse.search.nl1 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.search_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.nlBidi_3.1.0.jar[/email] [246] was not resolved.
!SUBENTRY 2 org.eclipse.help.nlBidi 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.help_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.forms.nl1_3.1.0.jar[/email] [248] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms.nl1 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.ui.forms_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.configurator.nl2_3.1.0.jar[/email] [249] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator.nl2 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.update.configurator_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.base.nl2_3.1.0.jar[/email] [251] was not resolved.
!SUBENTRY 2 org.eclipse.help.base.nl2 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.help.base_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.core.nlBidi_3.1.1.jar[/email] [252] was not resolved.
!SUBENTRY 2 org.eclipse.pde.core.nlBidi 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.pde.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.runtime.nl[/email]2_3.1.0/ [253] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.runtime.nl2 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.jdt.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.nl1_3.1.0.jar[/email] [254] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.nl1 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.jdt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.isv.nlBi[/email]di_3.1.1/ [261] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.isv.nlBidi 2 0 2007-08-21 12:12:27.042
!MESSAGE Missing host org.eclipse.jdt.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.042
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.source.nl[/email]2_3.1.1/ [262] was not resolved.
!SUBENTRY 2 org.eclipse.platform.source.nl2 2 0 2007-08-21 12:12:27.043
!MESSAGE Missing host org.eclipse.platform.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.043
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.nl1_3.1.1.jar[/email] [263] was not resolved.
!SUBENTRY 2 org.eclipse.jface.nl1 2 0 2007-08-21 12:12:27.043
!MESSAGE Missing host org.eclipse.jface_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.043
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.ui.nlBidi_3.1.1.jar[/email] [265] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.ui.nlBidi 2 0 2007-08-21 12:12:27.043
!MESSAGE Missing host org.eclipse.jdt.debug.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.user.nl[/email]1_3.1.1/ [266] was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.user.nl1 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.platform.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.compare.nl2_3.1.1.jar[/email] [270] was not resolved.
!SUBENTRY 2 org.eclipse.compare.nl2 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.compare_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nl[/email]2_3.1.1/ [274] was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nl2 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.nlBidi_3.1.0.jar[/email] [276] was not resolved.
!SUBENTRY 2 org.eclipse.pde.nlBidi 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.pde_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.texteditor.nl1_3.1.1.jar[/email] [279] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor.nl1 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.ui.workbench.texteditor_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.compare.nl1_3.1.1.jar[/email] [280] was not resolved.
!SUBENTRY 2 org.eclipse.compare.nl1 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.compare_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.nlBi[/email]di_3.1.1/ [281] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.nlBidi 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.jdt.junit_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.expressions.nlBidi_3.1.0.jar[/email] [285] was not resolved.
!SUBENTRY 2 org.eclipse.core.expressions.nlBidi 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.core.expressions_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.nlBidi_3.1.1.jar[/email] [288] was not resolved.
!SUBENTRY 2 org.eclipse.jface.nlBidi 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.jface_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.044
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.nl2_3.1.0.jar[/email] [289] was not resolved.
!SUBENTRY 2 org.eclipse.help.nl2 2 0 2007-08-21 12:12:27.044
!MESSAGE Missing host org.eclipse.help_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors.nlBidi_3.1.1.jar[/email] [291] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors.nlBidi 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.ui.editors_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.cheatsheets.nl1_3.1.1.jar[/email] [292] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets.nl1 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.ui.cheatsheets_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.nl[/email]2_3.1.1/ [294] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.nl2 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.jdt.debug_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.isv.nl[/email]1_3.1.1/ [295] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.isv.nl1 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.jdt.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.junit.runtime.nl[/email]1_3.1.0/ [297] was not resolved.
!SUBENTRY 2 org.eclipse.pde.junit.runtime.nl1 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.pde.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.core.nl1_3.1.1.jar[/email] [302] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.core.nl1 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.jdt.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.runtime.nl1_3.1.1.jar[/email] [304] was not resolved.
!SUBENTRY 2 org.eclipse.pde.runtime.nl1 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.pde.runtime_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core.nl2_3.1.1.jar[/email] [307] was not resolved.
!SUBENTRY 2 org.eclipse.team.core.nl2 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.team.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core.nl1_3.1.1.jar[/email] [308] was not resolved.
!SUBENTRY 2 org.eclipse.team.core.nl1 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.team.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.doc.user.nlBi[/email]di_3.1.1/ [310] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.doc.user.nlBidi 2 0 2007-08-21 12:12:27.045
!MESSAGE Missing host org.eclipse.jdt.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.045
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui.nl2_3.1.1.jar[/email] [311] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui.nl2 2 0 2007-08-21 12:12:27.046
!MESSAGE Missing host org.eclipse.team.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.046
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.doc.user.nlBi[/email]di_3.1.1/ [312] was not resolved.
!SUBENTRY 2 org.eclipse.pde.doc.user.nlBidi 2 0 2007-08-21 12:12:27.046
!MESSAGE Missing host org.eclipse.pde.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.046
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.isv.nl[/email]2_3.1.1/ [313] was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.isv.nl2 2 0 2007-08-21 12:12:27.046
!MESSAGE Missing host org.eclipse.platform.doc.isv_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.046
!MESSAGE Bundle [email]update@plugins/org.eclipse.compare.nlBidi_3.1.1.jar[/email] [316] was not resolved.
!SUBENTRY 2 org.eclipse.compare.nlBidi 2 0 2007-08-21 12:12:27.046
!MESSAGE Missing host org.eclipse.compare_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.046
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.core.nl1_3.1.1.jar[/email] [317] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.core.nl1 2 0 2007-08-21 12:12:27.046
!MESSAGE Missing host org.eclipse.team.cvs.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.046
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.debug.nl[/email]1_3.1.1/ [319] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.debug.nl1 2 0 2007-08-21 12:12:27.046
!MESSAGE Missing host org.eclipse.jdt.debug_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.046
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filebuffers.nlBidi_3.1.0.jar[/email] [320] was not resolved.
!SUBENTRY 2 org.eclipse.core.filebuffers.nlBidi 2 0 2007-08-21 12:12:27.046
!MESSAGE Missing host org.eclipse.core.filebuffers_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.046
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring.nl1_3.1.1.jar[/email] [323] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring.nl1 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.ltk.ui.refactoring_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.nlBidi_3.1.0.jar[/email] [325] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.nlBidi 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.jdt_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.source.nl[/email]1_3.1.1/ [327] was not resolved.
!SUBENTRY 2 org.eclipse.pde.source.nl1 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.pde.source_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.core.nl2_3.1.0.jar[/email] [329] was not resolved.
!SUBENTRY 2 org.eclipse.debug.core.nl2 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.debug.core_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.nl1_3.1.1.jar[/email] [330] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.nl1 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.ui.workbench_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh2.nl[/email]2_3.1.0/ [331] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ssh2.nl2 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.team.cvs.ssh2_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.doc.user.nlBi[/email]di/ [333] was not resolved.
!SUBENTRY 2 org.eclipse.platform.doc.user.nlBidi 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.platform.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.text.nlBidi_3.1.1.jar[/email] [335] was not resolved.
!SUBENTRY 2 org.eclipse.text.nlBidi 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.cheatsheets.nl2_3.1.1.jar[/email] [336] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets.nl2 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.ui.cheatsheets_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.047
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.base.nlBidi_3.1.0.jar[/email] [337] was not resolved.
!SUBENTRY 2 org.eclipse.help.base.nlBidi 2 0 2007-08-21 12:12:27.047
!MESSAGE Missing host org.eclipse.help.base_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.text.nl1_3.1.1.jar[/email] [338] was not resolved.
!SUBENTRY 2 org.eclipse.text.nl1 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.configurator.nl1_3.1.0.jar[/email] [339] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator.nl1 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.update.configurator_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.ui.nl2_3.1.1.jar[/email] [341] was not resolved.
!SUBENTRY 2 org.eclipse.pde.ui.nl2 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.pde.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.core.nl2_3.1.1.jar[/email] [342] was not resolved.
!SUBENTRY 2 org.eclipse.pde.core.nl2 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.pde.core_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.jface.text.nl1_3.1.1.jar[/email] [348] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text.nl1 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.jface.text_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.doc.user.nl[/email]1_3.1.1/ [350] was not resolved.
!SUBENTRY 2 org.eclipse.pde.doc.user.nl1 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.pde.doc.user_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.pde.build.nlBi[/email]di_3.1.0/ [351] was not resolved.
!SUBENTRY 2 org.eclipse.pde.build.nlBidi 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.pde.build_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.nlBi[/email]di_3.1.1/ [352] was not resolved.
!SUBENTRY 2 org.eclipse.platform.nlBidi 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.platform_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.ui.nl1_3.1.1.jar[/email] [353] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui.nl1 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.update.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.048
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.ui.nl2_3.1.1.jar[/email] [354] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui.nl2 2 0 2007-08-21 12:12:27.048
!MESSAGE Missing host org.eclipse.update.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.049
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ui.nl1_3.1.1.jar[/email] [361] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui.nl1 2 0 2007-08-21 12:12:27.049
!MESSAGE Missing host org.eclipse.team.cvs.ui_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.049
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.junit.runtime.nl[/email]1_3.1.0/ [362] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.junit.runtime.nl1 2 0 2007-08-21 12:12:27.049
!MESSAGE Missing host org.eclipse.jdt.junit.runtime_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.049
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro.nlBidi_3.1.1.jar[/email] [363] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.nlBidi 2 0 2007-08-21 12:12:27.049
!MESSAGE Missing host org.eclipse.ui.intro_[3.1.1,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.049
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.forms.nl2_3.1.0.jar[/email] [364] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms.nl2 2 0 2007-08-21 12:12:27.049
!MESSAGE Missing host org.eclipse.ui.forms_[3.1.0,3.2.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-21 12:12:27.049
!MESSAGE Bundle [email]update@plugins/org.eclipse.platform.source.nlBi[/email]di_3.1.1/ [366] was not resolved.
!SUBENTRY 2 org.eclipse.platform.source.nlBidi 2 0 2007-08-21 12:12:27.049
!MESSAGE Missing host org.eclipse.platform.source_[3.1.1,3.2.0).

!ENTRY org.eclipse.ui.workbench 4 0 2007-08-21 12:12:27.102
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.setBundleSL(StartLevelManager.java:718)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:452)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.ui.internal.WorkbenchPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   ...8 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.ui.internal.WorkbenchPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.setBundleSL(StartLevelManager.java:718)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:452)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

!ENTRY org.eclipse.ui.ide 4 0 2007-08-21 12:12:27.183
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.setBundleSL(StartLevelManager.java:718)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:452)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   ...8 more
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.setBundleSL(StartLevelManager.java:718)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:452)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

---

### Post by Jamie Jackson on 2007-08-22
Well, I can tell you that running Eclipse with libgcj makes for an unhappy Eclipse, but I didn't have any problems installing it with that. Did you run an apt-get purge to remove it? That might help.

Anyway, I run eclipse with a launcher that uses: "/usr/bin/eclipse -vm /usr/lib/jvm/java-6-sun/bin/java -vmargs -Xmx512M " to use the Sun Java.

Edit: Oh and you might want to delete your .eclipse and workspace directory before reinstalling, if you don't have anything you want to keep.

---

### Post by drekbour on 2007-09-01
I see the same dump files and clas loading errors as the OP (on Gutsy),  Have tried setting several JVMs via "eclipse -vm", "/etc/eclipse/java_home", Have reinstalled several times (via synaptic "complete-removal" of eclipse + related packages). no luck so far, the exact classes being reported as "missing" change from install to install (although SWTException is the most common - no surprising as it is probably the first swt class touched in classloading)   This is being reported in many threads on this forum.

ps.wtf? : sudo apt-get -s purge eclipse
E: Invalid operation purge

---

### Post by drekbour on 2007-09-01
Sorted. SWTException is (almost always) the first class a JVM tries to load from the SWT library.  the problem isn't directly with eclipse but with SWT. I purged and reinstalled libswt3.2-gtk-java to solve the problem (i was reinstalling eclipse at the same time so maybe this is required too).

Of course, that doesn't explain why things went wrong in the first place.

---

