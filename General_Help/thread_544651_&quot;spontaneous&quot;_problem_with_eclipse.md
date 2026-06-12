---
title: "&quot;spontaneous&quot; problem with eclipse"
date: 2007-09-06
forum: General Help
---

### Post by skelterjohn on 2007-09-06
I put spontaneous in quotes because I know that something must have changed, I just can't figure out what.

When I try to start eclipse now, I'm getting a few errors in my log that look like the stuff below. Does anyone know what might be going wrong or how to fix it?

[INDENT]
    org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
    [... snipping the stack trace ...]
    Root exception:
    java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError

    org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
    [... snip ...]
    Root exception:
    java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin

    org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
    [... snip ...][/INDENT]

---

### Post by lightstream on 2007-09-06
I use eclipse, but haven't had this problem.

Java NoClassDefFoundError exception is usually thrown when it cannot find the files containing the class.

How are you starting eclipse? What happens if you go to the command line and do:
```
cd /usr/lib/eclipse
./eclipse
```

---

