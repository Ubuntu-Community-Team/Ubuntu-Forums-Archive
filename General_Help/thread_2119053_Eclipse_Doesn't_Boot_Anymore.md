---
title: "Eclipse Doesn't Boot Anymore"
date: 2013-02-22
forum: General Help
---

### Post by shibby4555 on 2013-02-22
Tried booting it from root, got an error. Then tried regularily, got an error. Don't think I changed anything recently. I think I put in a Python IDE but thats it. Here's the log, anyone have this sort of problem before?

```

!ENTRY org.eclipse.osgi 4 0 2013-02-12 17:47:07.816
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons:
        no swt-gtk-3740 in java.library.path
        no swt-gtk in java.library.path
        Can't load library: /root/.swt/lib/linux/x86_64/libswt-gtk-3740.so
        Can't load library: /root/.swt/lib/linux/x86_64/libswt-gtk.so

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

```

---

