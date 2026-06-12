---
title: "Aptana Error On Opening"
date: 2019-01-20
forum: General Help
---

### Post by HerzeleidMeister on 2019-01-20
I've followed some tutorials online for installing/running Aptana. I've installed Java 11.02 and checked on the terminal that it is installed properly...

```
java 11.0.2 2018-10-16 LTSJava(TM) SE Runtime Environment 18.9 (build 11.0.2+7-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.2+7-LTS, mixed mode)

```

One of the tutorials stated that I need to set up a JAVA_HOME, and I followed the instructions but I'm not sure if it worked or not. Obviously at this point probably not lol. 

But when I double click on the "***AptanaStudio3***" file to run it, I get an error file that has to do with java. Any ideas how to fix this?

```
!SESSION 2019-01-20 07:50:52.105 -----------------------------------------------eclipse.buildId=unknown
java.version=11.0.2
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64


!ENTRY org.eclipse.osgi 4 0 2019-01-20 07:50:52.765
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
	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
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
	at java.base/java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:702)
	... 13 more
```

---

### Post by dragonfly41 on 2019-01-20
Although I now use Atom (atom.io) as my main IDE you can try this ..

Unzip Ubuntu Studio 3 into /opt/Aptana_Studio
Make /opt/Aptana_Studio/AptanaStudio3 as executable (69.8 KiB)
Place following .desktop file in ~/.local/share/applications/ as Aptana_Studio.desktop

```

[Desktop Entry]
Name=AptanaStudio3
Version=1.0
Comment=Aptana Studio 3
Exec=/opt/Aptana_Studio/AptanaStudio3
Icon=/opt/Aptana_Studio/icon.xpm
Terminal=false
Type=Application
Categories=Programming;

```

---

### Post by HerzeleidMeister on 2019-01-21
> **dragonfly41 said:**
> Although I now use Atom (atom.io) as my main IDE you can try this ..

Unzip Ubuntu Studio 3 into /opt/Aptana_Studio
Make /opt/Aptana_Studio/AptanaStudio3 as executable (69.8 KiB)
Place following .desktop file in ~/.local/share/applications/ as Aptana_Studio.desktop

```

[Desktop Entry]
Name=AptanaStudio3
Version=1.0
Comment=Aptana Studio 3
Exec=/opt/Aptana_Studio/AptanaStudio3
Icon=/opt/Aptana_Studio/icon.xpm
Terminal=false
Type=Application
Categories=Programming;

```

**Make /opt/Aptana_Studio/AptanaStudio3 as executable (69.8 KiB) **

How do I do this?

**Place following .desktop file in ~/.local/share/applications/ as Aptana_Studio.desktop**

And this?

---

### Post by dragonfly41 on 2019-01-21
Several ways to choose from .. by command line .. or perhaps just use your Files utility, navigate to AptanaStudio3 in /opt/
and then select the file and right click to bring up a properties window.

It seems that you will need to study basics about creating files and setting permissions.

From googling here is a thread selected at random. Saves repeating it.

[https://askubuntu.com/questions/484718/how-to-make-a-file-executable](https://askubuntu.com/questions/484718/how-to-make-a-file-executable)

---

