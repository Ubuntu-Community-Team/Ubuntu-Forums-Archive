---
title: "Problems with Eclipse (Wont load)"
date: 2007-08-30
forum: General Help
---

### Post by Lemons on 2007-08-30
Since this is my first post, I just wanna say how much I prefer Ubuntu over Windows ^^ Its alot nicer and cleaner, and beryl is kinda what brought me over. Setting up everything takes a bit, but well worth the time (No stress really, except permissions at first :P).

Onto the problem

I have tried starting eclipse, and get the following error:

```

!SESSION 2007-08-30 22:43:47.553 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-08-30 22:43:51.807
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-30 22:43:51.807
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-30 22:43:51.807
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-30 22:43:51.807
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2007-08-30 22:43:53.081
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2007-08-30 22:43:53.257
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (69).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
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
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /Devias Server/.project not found.
   at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
   at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
   at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
   at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
   at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
   at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
   at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
   at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
   at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
   at java.security.AccessController.doPrivileged(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
   ...25 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /Devias Server/.project not found.
   at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
   at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
   at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
   at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
   at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
   at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
   at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
   at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
   at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
   at java.security.AccessController.doPrivileged(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
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
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-08-30 22:43:53.347
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...11 more

!ENTRY org.eclipse.osgi 2 0 2007-08-30 22:43:53.454
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-08-30 22:43:53.454
!MESSAGE Bundle update@../../../home/kris/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.pde.runtime_3.1.1.jar [119] was not resolved.

```

This happened after my computer froze, and ive read that this has happened to similar people. I have tried some suggestions, like reinstall Eclipse/Java and clear the ~/eclipse and ~/workspace folders, and havnt worked :S

It stops loading before the loading bar even comes up.

Any help is appreciated, wanna get to some java coding ^^

If this is the wrong section, sorry :S Didnt know if it would be in here or Installing and Updating... Should be fine though ^^'

EDIT: Fixed, deleted eclipse instead of .eclipse, now that i did, everythings fine ^^

---

