---
title: "Eclipse installer throws startup errors in Ubuntu 18.04"
date: 2019-05-24
forum: General Help
---

### Post by tinohost on 2019-05-24
[COLOR=#242729][FONT=Arial]While running the Eclipse installer I am getting this message.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit][COLOR=rgba(220, 70, 29, 0.701960784313725)][IMG]https://i.stack.imgur.com/bdH1A.png[/IMG][/FONT][/FONT][/COLOR][/COLOR]
[COLOR=#242729][FONT=Arial]In the configuration log the following is written[/FONT][/COLOR]

```
!SESSION 2019-05-24 10:56:46.029 -----------------------------------------------
eclipse.buildId=4.3.2.M20140221-1700
java.version=12.0.1
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_IN
Framework arguments:  -product org.eclipse.epp.package.cpp.product
Command-line arguments:  -os linux -ws gtk -arch x86_64 -product org.eclipse.epp.package.cpp.product

!ENTRY org.eclipse.osgi 4 0 2019-05-24 10:56:46.345
!MESSAGE Startup error
!STACK 1
java.lang.RuntimeException: Exception in org.eclipse.osgi.framework.internal.core.SystemBundleActivator.start() of bundle org.eclipse.osgi.
    at org.eclipse.osgi.framework.internal.core.InternalSystemBundle.resume(InternalSystemBundle.java:233)
    at org.eclipse.osgi.framework.internal.core.Framework.launch(Framework.java:656)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:275)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.base/java.lang.reflect.Method.invoke(Method.java:567)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:636)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:591)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1450)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1426)
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.osgi.framework.internal.core.SystemBundleActivator.start() of bundle org.eclipse.osgi.
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:734)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:683)
    at org.eclipse.osgi.framework.internal.core.InternalSystemBundle.resume(InternalSystemBundle.java:225)
    ... 11 more
Caused by: java.lang.IllegalStateException: The System Bundle could not be resolved: Missing Constraint: Bundle-RequiredExecutionEnvironment: J2SE-1.5
    at org.eclipse.osgi.internal.baseadaptor.BaseStorage.checkSystemState(BaseStorage.java:827)
    at org.eclipse.osgi.internal.baseadaptor.BaseStorage.getStateManager(BaseStorage.java:800)
    at org.eclipse.osgi.baseadaptor.BaseAdaptor.getState(BaseAdaptor.java:387)
    at org.eclipse.osgi.internal.baseadaptor.BaseStorage.frameworkStart(BaseStorage.java:923)
    at org.eclipse.osgi.baseadaptor.BaseAdaptor.frameworkStart(BaseAdaptor.java:250)
    at org.eclipse.osgi.framework.internal.core.SystemBundleActivator.start(SystemBundleActivator.java:60)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:711)
    at java.base/java.security.AccessController.doPrivileged(AccessController.java:551)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:702)
    ... 13 more

```

N&#7871;u b&#7841;n c&#7847;n m&#7897;t công ty chuyên cung c&#7845;p [hosting giá r&#7867;]("https://tinohost.com/hosting") ch&#7845;t l&#432;&#7907;ng cao &#273;áp &#7913;ng &#273;&#432;&#7907;c các tiêu chí giúp b&#7841;n phát tri&#7875;n toàn di&#7879;n thì [tino host]("https://tinohost.com/") là công ty s&#7889; 1 hi&#7879;n nay

---

### Post by coffeecat on 2019-05-24
> [color=red][size=3]Forum Feedback and Help is not for general support enquiries[/size][/color]

*Thread moved to **General Help**.*

---

