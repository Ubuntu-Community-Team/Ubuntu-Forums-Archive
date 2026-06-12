---
title: "Eclipse error"
date: 2005-04-06
forum: General Help
---

### Post by droogie on 2005-04-06
I installed the latest version of java and now I want to install eclipse.  I downloaded what I think is the right version, unpacked it and tried to run it and this is the error I get.

!SESSION 2005-04-06 22:45:27.475 -----------------------------------------------
eclipse.buildId=I20050219-1500
java.fullversion=GNU libgcj 3.3.4 (Debian 1:3.3.4-9ubuntu5)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2005-04-06 22:45:27.479
!MESSAGE Startup error
!STACK 1
java.lang.LinkageError: unexpected exception during linking: org.eclipse.core.runtime.adaptor.EclipseAdaptor
   at java.lang.ClassLoader.resolveClass0(java.lang.Class) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.4.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.4.0.0)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.createAdaptor() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(java.lang.String[], java.lang.Runnable) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.String[], java.lang.Runnable) (Unknown Source)
   at _Jv_CallAnyMethodA(java.lang.Object, java.lang.Class, _Jv_Method, boolean, java.lang.Class[], jvalue, jvalue) (/usr/lib/libgcj.so.4.0.0)
   at _Jv_CallAnyMethodA(java.lang.Object, java.lang.Class, _Jv_Method, boolean, java.lang.Class[], java.lang.Object[]) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.reflect.Method.invoke(java.lang.Object, java.lang.Object[]) (/usr/lib/libgcj.so.4.0.0)
   at org.eclipse.core.launcher.Main.invokeFramework(java.lang.String[], java.net.URL[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.basicRun(java.lang.String[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.run(java.lang.String[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.main(java.lang.String[]) (Unknown Source)
Caused by: java.lang.InternalError: Unexpected exception while defining class org.eclipse.core.runtime.adaptor.PluginParser
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.4.0.0)
   at java.security.SecureClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.CodeSource) (/usr/lib/libgcj.so.4.0.0)
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.4.0.0)
   at _Jv_FindClass(_Jv_Utf8Const, java.lang.ClassLoader) (/usr/lib/libgcj.so.4.0.0)
   at _Jv_PrepareCompiledClass(java.lang.Class) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.ClassLoader.linkClass0(java.lang.Class) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.ClassLoader.resolveClass0(java.lang.Class) (/usr/lib/libgcj.so.4.0.0)
   ...13 more
Caused by: java.lang.ClassNotFoundException: org.xml.sax.helpers.DefaultHandler not found in [file:/home/mrasmussen/eclipse/plugins/org.eclipse.osgi_3.1.0/core.jar, file:/home/mrasmussen/eclipse/plugins/org.eclipse.osgi_3.1.0/console.jar, file:/home/mrasmussen/eclipse/plugins/org.eclipse.osgi_3.1.0/eclipseAdaptor.jar]
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.4.0.0)
   at _Jv_FindClass(_Jv_Utf8Const, java.lang.ClassLoader) (/usr/lib/libgcj.so.4.0.0)
   at _Jv_ClassReader.handleClassBegin(int, int, int) (/usr/lib/libgcj.so.4.0.0)
   at _Jv_ClassReader.parse() (/usr/lib/libgcj.so.4.0.0)
   at _Jv_DefineClass(java.lang.Class, byte[], int, int) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.ClassLoader.defineClass0(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.4.0.0)
   ...20 more
!SESSION Wed Apr 06 22:45:27 GMT-05:00 2005 ------------------------------------
!ENTRY org.eclipse.core.launcher 4 0 Apr 06, 2005 22:45:27.657
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.NullPointerException
   at _Jv_CallAnyMethodA(java.lang.Object, java.lang.Class, _Jv_Method, boolean, java.lang.Class[], jvalue, jvalue) (/usr/lib/libgcj.so.4.0.0)
   at _Jv_CallAnyMethodA(java.lang.Object, java.lang.Class, _Jv_Method, boolean, java.lang.Class[], java.lang.Object[]) (/usr/lib/libgcj.so.4.0.0)
   at java.lang.reflect.Method.invoke(java.lang.Object, java.lang.Object[]) (/usr/lib/libgcj.so.4.0.0)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.String[], java.lang.Runnable) (Unknown Source)
   at org.eclipse.core.launcher.Main.invokeFramework(java.lang.String[], java.net.URL[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.basicRun(java.lang.String[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.run(java.lang.String[]) (Unknown Source)

Any ideas??

-Mike
:: Edited for spelling

---

### Post by bonifacio on 2005-04-06
see [this](http://www.ubuntuforums.org/showthread.php?t=24276)

---

### Post by Johan on 2005-04-07
Strange, it works for me. How much space do you have available on your partitions? Which jvm are you using and which version is it?

---

### Post by Johan on 2005-04-09
It seems like the latest version of eclipse requires the jdk1.5.

---

