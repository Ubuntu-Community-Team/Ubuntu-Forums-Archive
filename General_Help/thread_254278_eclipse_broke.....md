---
title: "eclipse broke...."
date: 2006-09-09
forum: General Help
---

### Post by hollaburoo on 2006-09-09
Somehow I managed to break eclipse.  When I try to run it I the splash screen shows up bu then I get an error message telling me to check the log.  Here's what I found as the latest entry, if anyone thinks it can help:

```

!SESSION 2006-09-09 17:47:53.752 -----------------------------------------------
eclipse.buildId=M20060118-1600
java.fullversion=GNU libgcj 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.resources 2 10035 2006-09-09 17:48:05.389
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.core.resources 4 567 2006-09-09 17:48:05.597
!MESSAGE Workspace restored, but some problems occurred.
!SUBENTRY 1 org.eclipse.core.resources 4 567 2006-09-09 17:48:05.597
!MESSAGE The project description file (.project) for RecursiveMath is missing.  This file contains important information about the project.  The project will not function properly until this file is restored.

!ENTRY org.eclipse.osgi 2006-09-09 17:48:05.612
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (31).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1013)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:969)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:318)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:97)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:279)
   at org.eclipse.core.launcher.Main.run(Main.java:974)
   at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /rampblecs/Ramblecs.class not found.
   at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
   at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:586)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
   at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
   at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:793)
   at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
   at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:647)
   at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1302)
   at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1876)
   at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1646)
   at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:357)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:995)
   at java.security.AccessController.doPrivileged(libgcj.so.7)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:988)
   ...21 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /rampblecs/Ramblecs.class not found.
   at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
   at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:586)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
   at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
   at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
   at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
   at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:793)
   at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
   at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:647)
   at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1302)
   at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1876)
   at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1646)
   at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:357)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:995)
   at java.security.AccessController.doPrivileged(libgcj.so.7)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:988)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:969)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:318)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:97)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:279)
   at org.eclipse.core.launcher.Main.run(Main.java:974)
   at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2006-09-09 17:48:06.162
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor
   at java.lang.Class.initializeClass(libgcj.so.7)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:97)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:279)
   at org.eclipse.core.launcher.Main.run(Main.java:974)
   at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IWorkspace
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:405)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...9 more
```

---

### Post by revenant_org on 2006-09-10
The same here ](*,) , I also tried eclipse from eclipse.org but no luck.

Edit: Solved, you need to modify /etc/eclipse by commenting gcj.
check [http://www.ubuntuforums.org/showthread.php?t=253359&highlight=eclipse]("http://www.ubuntuforums.org/showthread.php?t=253359&highlight=eclipse") for more details.

---

### Post by hollaburoo on 2006-09-11
Unfortunately its still not working, I think I'm going to install Edgy Eft anyway though.

---

### Post by sisooktom on 2006-09-12
Your best bet is to install a real JDK (meaning not gcj) and the official Eclipse from eclipse.org.  Note that the official version will not run at all with gcj, nor will pretty much any other java app you download.

---

