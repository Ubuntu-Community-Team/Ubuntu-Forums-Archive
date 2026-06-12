---
title: "Unable to launch Eclipse"
date: 2018-06-07
forum: General Help
---

### Post by wylieza on 2018-06-07
When I try launch eclipse, its show the splash screen. Then it asks where I would like to have my workspace, after selecting that it shows a dialog that states that it has failed to lauch and I should check the log file.

I have had a look at the log file, but I am not entirely sure what the problem is (I can't make out what the log file is saying). I have tried deleting the workspace and the eclipse folder and then rextracting it. This has not helped.

I am running Ubuntu 18. 

I did have eclipse installed and working earlier using umake, but decided I would rather just do it "manually" so I uninstalled umake and deleted the files related to eclipse from that installation.

Here is the output from the log file:

```
!SESSION 2018-06-07 18:12:26.032 -----------------------------------------------eclipse.buildId=4.7.3.M20180330-0640
java.version=10.0.1
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_ZA
Framework arguments:  -product org.eclipse.epp.package.cpp.product
Command-line arguments:  -os linux -ws gtk -arch x86_64 -product org.eclipse.epp.package.cpp.product


!ENTRY org.eclipse.osgi 4 0 2018-06-07 18:12:43.050
!MESSAGE Application error
!STACK 1
org.eclipse.e4.core.di.InjectionException: java.lang.NoClassDefFoundError: javax/annotation/PostConstruct
    at org.eclipse.e4.core.internal.di.InjectorImpl.internalMake(InjectorImpl.java:410)
    at org.eclipse.e4.core.internal.di.InjectorImpl.make(InjectorImpl.java:318)
    at org.eclipse.e4.core.contexts.ContextInjectionFactory.make(ContextInjectionFactory.java:162)
    at org.eclipse.e4.ui.internal.workbench.swt.E4Application.createDefaultHeadlessContext(E4Application.java:491)
    at org.eclipse.e4.ui.internal.workbench.swt.E4Application.createDefaultContext(E4Application.java:505)
    at org.eclipse.e4.ui.internal.workbench.swt.E4Application.createE4Workbench(E4Application.java:204)
    at org.eclipse.ui.internal.Workbench.lambda$3(Workbench.java:614)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:336)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:594)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:148)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:151)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:134)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:104)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:388)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:243)
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.base/java.lang.reflect.Method.invoke(Method.java:564)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:653)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:590)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1499)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1472)
Caused by: java.lang.NoClassDefFoundError: javax/annotation/PostConstruct
    at org.eclipse.e4.core.internal.di.InjectorImpl.inject(InjectorImpl.java:124)
    at org.eclipse.e4.core.internal.di.InjectorImpl.internalMake(InjectorImpl.java:399)
    ... 23 more
Caused by: java.lang.ClassNotFoundException: javax.annotation.PostConstruct cannot be found by org.eclipse.e4.core.di_1.6.100.v20170421-1418
    at org.eclipse.osgi.internal.loader.BundleLoader.findClassInternal(BundleLoader.java:433)
    at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:395)
    at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:387)
    at org.eclipse.osgi.internal.loader.ModuleClassLoader.loadClass(ModuleClassLoader.java:150)
    at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:499)
    ... 25 more


!ENTRY org.eclipse.e4.ui.workbench 4 0 2018-06-07 18:12:43.073
!MESSAGE FrameworkEvent ERROR
!STACK 0
java.lang.NoClassDefFoundError: javax/annotation/PreDestroy
    at org.eclipse.e4.core.internal.di.InjectorImpl.disposed(InjectorImpl.java:450)
    at org.eclipse.e4.core.internal.di.Requestor.disposed(Requestor.java:156)
    at org.eclipse.e4.core.internal.contexts.ContextObjectSupplier$ContextInjectionListener.update(ContextObjectSupplier.java:78)
    at org.eclipse.e4.core.internal.contexts.TrackableComputationExt.update(TrackableComputationExt.java:111)
    at org.eclipse.e4.core.internal.contexts.TrackableComputationExt.handleInvalid(TrackableComputationExt.java:74)
    at org.eclipse.e4.core.internal.contexts.EclipseContext.dispose(EclipseContext.java:178)
    at org.eclipse.e4.core.internal.contexts.osgi.EclipseContextOSGi.dispose(EclipseContextOSGi.java:99)
    at org.eclipse.e4.core.internal.contexts.osgi.EclipseContextOSGi.bundleChanged(EclipseContextOSGi.java:141)
    at org.eclipse.osgi.internal.framework.BundleContextImpl.dispatchEvent(BundleContextImpl.java:908)
    at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:230)
    at org.eclipse.osgi.framework.eventmgr.ListenerQueue.dispatchEventSynchronous(ListenerQueue.java:148)
    at org.eclipse.osgi.internal.framework.EquinoxEventPublisher.publishBundleEventPrivileged(EquinoxEventPublisher.java:213)
    at org.eclipse.osgi.internal.framework.EquinoxEventPublisher.publishBundleEvent(EquinoxEventPublisher.java:120)
    at org.eclipse.osgi.internal.framework.EquinoxEventPublisher.publishBundleEvent(EquinoxEventPublisher.java:112)
    at org.eclipse.osgi.internal.framework.EquinoxContainerAdaptor.publishModuleEvent(EquinoxContainerAdaptor.java:168)
    at org.eclipse.osgi.container.Module.publishEvent(Module.java:476)
    at org.eclipse.osgi.container.Module.doStop(Module.java:634)
    at org.eclipse.osgi.container.Module.stop(Module.java:498)
    at org.eclipse.osgi.container.SystemModule.stop(SystemModule.java:202)
    at org.eclipse.osgi.internal.framework.EquinoxBundle$SystemBundle$EquinoxSystemModule$1.run(EquinoxBundle.java:165)
    at java.base/java.lang.Thread.run(Thread.java:844)
Caused by: java.lang.ClassNotFoundException: javax.annotation.PreDestroy cannot be found by org.eclipse.e4.core.di_1.6.100.v20170421-1418
    at org.eclipse.osgi.internal.loader.BundleLoader.findClassInternal(BundleLoader.java:433)
    at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:395)
    at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:387)
    at org.eclipse.osgi.internal.loader.ModuleClassLoader.loadClass(ModuleClassLoader.java:150)
    at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:499)
    ... 21 more
```

---

### Post by wylieza on 2018-06-08
This can be solved by setting the VM that Eclipse should use in the eclipse.ini file.

More here:
[https://www.eclipse.org/forums/index.php/t/198527/](https://www.eclipse.org/forums/index.php/t/198527/)

---

