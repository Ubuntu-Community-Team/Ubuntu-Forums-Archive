---
title: "Best way to install Eclipse?"
date: 2005-10-15
forum: General Help
---

### Post by veraction on 2005-10-15
Ok, I had it working great in Hoary, but trying to upgrade to Breezy completely f'ed up my system, so I am now working with a fresh install of Breezy.

I tried Applications -> Add Applications -> Eclipse and I tried installing all eclipse packages from synaptic, however they always have some problems, either loading plugins or other issues.

Is there a simple/clean way to do it?

And, if I use the program from [eclipse.org]("http://eclipse.org"), where should I put all the files, so that I can have a normal running program? (i.e. where to put stuff in /etc, /opt, /usr/share, etc.)

---

### Post by Rogmo on 2005-10-15
Take a look in here 


[https://wiki.ubuntu.com/EclipseIDE](https://wiki.ubuntu.com/EclipseIDE)

Good luck :)

---

### Post by veraction on 2005-10-15
yeah, I saw that. it seems very dated. 

Think I'll be going back to Hoary soon if I can't figure this out in a reasonable time (plus a few other annoyances)

---

### Post by Rogmo on 2005-10-15
Here seems to be other people with same problems

[http://www.ubuntuforums.org/showthread.php?t=76300](http://www.ubuntuforums.org/showthread.php?t=76300)


Hopefully they will find a solution

---

### Post by l.tambiah on 2005-10-15
Dont install eclipse via apt get. Goto the link [https://wiki.ubuntu.com/EclipseIDE]("https://wiki.ubuntu.com/EclipseIDE")
and install it manually by downloading the latest eclipse build from the eclipse website. I have installed Eclipse as a global installation and is working fine.

---

### Post by BIGtrouble77 on 2005-10-15
I think it's best to just download eclipse manually.  You don't even have to install/compile it.  It just runs as long as java is properly installed.

My webapp runs on sun's java so breezy's eclipse is useless to me.  It fact, it's been causing me a lot of headaches.  It's extremely slow and appears to be using more system resources than it should.

Eclipse is too easy to get going to be dealing with this.  I understand why ubuntu uses the version of java it does, unfortunately that doesn't help people who have been developing on sun's java for years.  I actually have a backup copy of eclipse with all of it's plugins sitting on my usb drive for whenever I have to reconfigure my system.  It's literally drag and drop.  The problems I usually have are tomcat write permissions and mysql case sensativity issues.

---

### Post by l.tambiah on 2005-10-16
Unfortunateley suns jsdk isnt open source as of yet. Sun seem to be hanging on to it, it would be nice if they open sourced it though. We can't be to harsh on Sun as they have open soured a few projects such as the great openOffice. Thinking of that makes me feel better when using the sun proprietry java development kit. 

Blackdown Java, GCJ would be fine for certain programmers as they can choose there classes as they write the code, however for applications such as eclipse it could rely on some of sun's jdk classes.

---

### Post by galderz on 2005-12-20
just installed downloading it from the eclipse website but when i open it, eveything under the button bar is empty, nothing can be opened.

checked and the JDT is installed, i have GTK2 installed too.

anyone come across anything similar?

---

### Post by galderz on 2005-12-20
just checked the log and apparently it says out of memory. the workspace is in my home area and there's about 8 gb left in it. The main has 2gb left.

Has anyone seen anything like this?

!ENTRY org.eclipse.osgi 2005-12-21 00:33:37.412
!MESSAGE An error occurred while automatically activating bundle org.eclipse.jdt.core (89).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.jdt.core.JavaCore.start() of bundle org.eclipse.jdt.core.
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._Z26_Jv_FindClassFromSignaturePcPN4java4lang11ClassLoaderE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier12pop_init_refENS_4typeE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier21verify_instructions_0Ev (/usr/lib/libgcj.so.6.0.0)
   at ._Z16_Jv_VerifyMethodP16_Jv_InterpMethod (/usr/lib/libgcj.so.6.0.0)
   at ._ZN21_Jv_InterpreterEngine9do_verifyEPN4java4lang5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN10_Jv_Linker12verify_classEPN4java4lang5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN10_Jv_Linker14wait_for_stateEPN4java4lang5ClassEi (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader12resolveClassEPNS0_5ClassE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang7reflect11Constructor11newInstanceEP6JArrayIPNS0_6ObjectEE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.plugins.PluginDescriptor.internalDoPluginActivation() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.plugins.PluginDescriptor.doPluginActivation() (Unknown Source)
   at ._ZN16_Jv_InterpMethod16run_synch_objectEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.plugins.PluginDescriptor.getPlugin() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(org.osgi.framework.BundleContext) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java8security16AccessController12doPrivilegedEPNS0_25PrivilegedExceptionActionE (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at ._ZN16_Jv_InterpMethod10run_normalEP7ffi_cifPvP7ffi_rawS2_ (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.OutOfMemoryError
   <<No stacktrace available>>
Root exception:
java.lang.OutOfMemoryError
   <<No stacktrace available>>

---

### Post by spier on 2005-12-20
[QUOTE=galderz]just installed downloading it from the eclipse website but when i open it, eveything under the button bar is empty, nothing can be opened.

checked and the JDT is installed, i have GTK2 installed too.

anyone come across anything similar?[/QUOTE]

Seems like what I got the first time I tried to install Eclipse from eclipse.org.

Experimenting around, I installed sun java sdk 1.5  and after selecting it through

 sudo update-alternatives --config java

I got Eclipse working!

---

### Post by neurosis on 2005-12-20
I always install Eclipse locally in my home folder under ~/eclipse. Never had any issues!

---

### Post by garukun on 2007-09-08
I installed the eclipse from the Synaptics, but i got this error that redirects to look at the log file, 
here is the log file, any one know what's going on? 

Seems like a plugin is missing or something.

Thanks in advance!

```

!SESSION 2007-09-08 13:41:54.093 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-09-08 13:41:57.006
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-09-08 13:41:57.006
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-09-08 13:41:57.007
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-09-08 13:41:57.007
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-09-08 13:41:57.085
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (79).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
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
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   ...58 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...61 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
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
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...61 more

!ENTRY org.eclipse.osgi 4 0 2007-09-08 13:41:57.152
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (67).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   ...29 more
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-09-08 13:41:57.166
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.throwException(RegistryStrategyOSGI.java:165)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:149)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
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

---

