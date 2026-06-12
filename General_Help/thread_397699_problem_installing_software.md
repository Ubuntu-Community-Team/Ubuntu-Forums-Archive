---
title: "problem installing software"
date: 2007-03-31
forum: General Help
---

### Post by jenny_psion on 2007-03-31
Hello, 

I am not sure if this is the right forum for this, but here we go...

I am running Kubuntu on VMware Player on my laptop, and I just tried to install some software that is based on Eclipse. For some strange reason I get a huge error log, which find very strange because if I run Eclipse I do not get any errors.

I would be glad if someone could help.

```
!SESSION 2007-03-30 22:43:17.290 -----------------------------------------------
eclipse.buildId=unknown
java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.core.runtime 2007-03-30 22:43:19.361
!MESSAGE Product org.rodinp.platform.product could not be found.

!ENTRY org.eclipse.osgi 4 0 2007-03-30 22:43:19.381
!MESSAGE Application error
!STACK 1
java.lang.RuntimeException: No application id has been found.
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:56)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```

There is a second part to this error message, so if anyone can help, I can add it to the thread.

Thanks.
psion

---

