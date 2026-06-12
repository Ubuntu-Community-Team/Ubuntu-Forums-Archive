---
title: "Eclipse Indigo (Java) crashes at start up"
date: 2012-12-03
forum: General Help
---

### Post by zobayer1 on 2012-12-03
I am using ubuntu 12.04 x64 edition. Yesterday I installed Eclipse through Ubuntu Software Center. After being successfully installed, I can't start it, cause it fails showing a fatal error message. Then I checked the log file which looks like this.
```

!SESSION 2012-12-04 01:56:24.030 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_09
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2012-12-04 01:56:24.804
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
    no swt-gtk-3740 in java.library.path
    no swt-gtk in java.library.path
    Can't load library: /home/zobayer/.swt/lib/linux/x86_64/libswt-gtk-3740.so
    Can't load library: /home/zobayer/.swt/lib/linux/x86_64/libswt-gtk.so

    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:285)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
    at org.eclipse.swt.internal.C.<clinit>(C.java:21)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
    at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:695)
    at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
    at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:153)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:95)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:601)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1410)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1386)

```

Do I need to install additional package? Or I need to set some environmental variables for those missing libraries. I used Eclipse before on both windows and earlier versions of ubuntu, never seen any such thing. Or should I download the binary from Eclipse site?

Thanks in advance.

---

### Post by zobayer1 on 2012-12-03
Ahh, solved, I was not looking at the right place. How ever, looks like the paths were odd. So the following command worked for me.
```

ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64/

```

for 32 bit version, the last part will be only x86

I found this solution on [stackoverflow]("http://stackoverflow.com/questions/10165693/eclipse-cannot-load-swt-libraries")

---

