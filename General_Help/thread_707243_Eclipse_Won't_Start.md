---
title: "Eclipse Won't Start"
date: 2008-02-25
forum: General Help
---

### Post by NetSpike on 2008-02-25
Hi

My Eclipse crashed about 6 times today, and the 7th time it shows the following error message when I launch it:

An error has occurred. See the log file
/home/emarran/workspace/.metadata/.log.


The .log file's contents is as follows (sorry, it's quite messy):

!SESSION 2008-02-25 14:21:59.108 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_03
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_ZA
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-02-25 14:22:02.830
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-02-25 14:22:02.831
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-02-25 14:22:02.831
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-02-25 14:22:02.831
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-02-25 14:22:03.935
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-02-25 14:22:03.955
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (26).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
    at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:8
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:7
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /domaintransfer/includes/classes/class.domain_transfer_manager.php not found.
    at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
    at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
    at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
    at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
    at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
    at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:8
    at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
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
    at java.security.AccessController.doPrivileged(Native Method)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
    ... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /domaintransfer/includes/classes/class.domain_transfer_manager.php not found.
    at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
    at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
    at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
    at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
    at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
    at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
    at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
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
    at java.security.AccessController.doPrivileged(Native Method)
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
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-02-25 14:22:03.967
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2008-02-25 14:22:04.009
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-02-25 14:22:04.009
!MESSAGE Bundle [EMAIL="update@../../../home/emarran/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.pde.runtime_3.1.1.jar"]update@../../../home/emarran/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.pde.runtime_3.1.1.jar[/EMAIL] 125 was not resolved.


Could anyone please help as I need to continue with work ASAP.

Thanks in advance!

Edward

---

### Post by SOULRiDER on 2008-02-25
No idea, in the meanwhile you could try using easyeclipse ( [http://easyeclipse.org](http://easyeclipse.org) ) while you wait for someoen that knows whats causing it.

---

### Post by brakbox on 2008-03-04
Had the same problem today. Hope this helps:

mv workspace workspace_old
restart eclipse and import you projects

Did the trick for me.
Got it from: [http://ubuntuforums.org/showthread.php?p=2919550](http://ubuntuforums.org/showthread.php?p=2919550)

---

### Post by swathij_jangam on 2008-05-16
Hi all,i have problem running struts project on tomcat through eclipse ide,i have properly installed tomcat and configured it to eclipse,but i don't know where it goes wrong and gives dis message
Publishing the configuration:
could not publish server configuration:
Resource is out of sync with the file system./Server/Tomcatv 5.5 sever
pls any help is greatly appreciated

---

