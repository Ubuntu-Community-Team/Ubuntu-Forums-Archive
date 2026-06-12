---
title: "Eclipse Error Log"
date: 2006-10-27
forum: General Help
---

### Post by Paul41 on 2006-10-27
I have upgraded to Edgy and ever since then when I try to open a php file in Eclipse it says 
> An error has occurred. See error log for more details.
I haven't been able to find the error log for Eclipse. Does anyone know where it it?

Has anyone else had this problem? I am using phpEclipse. I can open any type of file but a php file.

---

### Post by Paul41 on 2006-10-28
I have now noticed that when I try to create a new php file there is a problem also. The file gets created, but it just brings up a blank tab. Then the new file acts like the other files where I get an error when I try to open it. I initially thought it could be a permissions problem, but I checked that and everything was OK. I am able to open and work with these same files in Screem with no problem.

---

### Post by utopyr on 2006-10-29
It might be referring to the one in /home/*username*/workspace/.metadata/.log

---

### Post by nife on 2006-10-29
I am having trouble with eclipse now too.  On an adm64 machine I am getting an error with eclipse and azureus.  Both are complaining about memmove

Here is the error log for eclipse.  Looks like swt is not compiled correctly for 64 bit arch.

```
!SESSION 2006-10-29 14:54:40.076 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2006-10-29 14:54:44.758
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-10-29 14:54:44.759
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-10-29 14:54:44.759
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2006-10-29 14:54:44.759
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2006-10-29 14:54:45.079
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
	at org.eclipse.swt.internal.gtk.OS.memmove(Native Method)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

```

Azureus gives the same error with a little less of a stack trace.

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: memmove
        at org.eclipse.swt.internal.gtk.OS.memmove(Native Method)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:80)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162
```

---

### Post by Paul41 on 2006-10-29
> /home/username/workspace/.metadata/.log
Here is what was in this log. I don't see anything here that would be causing my problem.

```
!SESSION 2006-06-25 23:11:43.594 -----------------------------------------------
eclipse.buildId=M20060118-1600
java.fullversion=GNU libgcj 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.update.configurator 2006-06-25 23:11:47.470
!MESSAGE Could not install bundle ../../../home/psanders1/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.pde.runtime_3.1.1.jar   Bundle "org.eclipse.pde.runtime" version "3.1.1" has already been installed from: update@plugins/org.eclipse.pde.runtime_3.1.1.jar

!ENTRY org.eclipse.update.core 4 0 2006-06-25 23:13:17.195
!MESSAGE UpdateManagerUtils copy() at offset:20424 [InputStream ended after 20424 bytes (expected 4747 )]
!STACK 0
java.io.IOException: InputStream ended after 20424 bytes (expected 4747 )
   at org.eclipse.update.internal.core.UpdateManagerUtils.copy(UpdateManagerUtils.java:897)
   at org.eclipse.update.core.FeatureContentProvider.asLocalReference(FeatureContentProvider.java:278)
   at org.eclipse.update.internal.core.FeaturePackagedContentProvider.getFeatureEntryArchiveReferences(FeaturePackagedContentProvider.java:143)
   at org.eclipse.update.internal.core.FeaturePackagedContentProvider.getFeatureManifestReference(FeaturePackagedContentProvider.java:69)
   at org.eclipse.update.internal.core.FeaturePackagedFactory.createFeature(FeaturePackagedFactory.java:39)
   at org.eclipse.update.core.Site.createFeature(Site.java:515)
   at org.eclipse.update.core.FeatureReference.createFeature(FeatureReference.java:117)
   at org.eclipse.update.core.FeatureReference.getFeature(FeatureReference.java:105)
   at org.eclipse.update.core.FeatureReference.getFeature(FeatureReference.java:92)
   at org.eclipse.update.internal.search.SiteSearchCategory$Query.run(SiteSearchCategory.java:63)
   at org.eclipse.update.search.UpdateSearchRequest.searchOneSite(UpdateSearchRequest.java:393)
   at org.eclipse.update.search.UpdateSearchRequest.performSearch(UpdateSearchRequest.java:278)
   at org.eclipse.update.ui.UpdateJob.runSearchForNew(UpdateJob.java:178)
   at org.eclipse.update.ui.UpdateJob.run(UpdateJob.java:165)
   at org.eclipse.core.internal.jobs.Worker.run(Worker.java:76)
!SESSION 2006-06-25 23:06:47.832 -----------------------------------------------
eclipse.buildId=M20060118-1600
java.fullversion=GNU libgcj 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.update.configurator 2006-06-25 23:06:57.28
!MESSAGE Could not install bundle ../../../home/psanders1/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.pde.runtime_3.1.1.jar   Bundle "org.eclipse.pde.runtime" version "3.1.1" has already been installed from: update@plugins/org.eclipse.pde.runtime_3.1.1.jar
```

---

### Post by risbac on 2006-10-31
Same problem, with PHP files, with different JVMs. I tried with the gjc, and with Sun's one. Can't find a solution yet, so it's really extremely annoying. Thanks in advance if anyone has a solution, I didn't find any on various forums or websites yet...

---

### Post by Paul41 on 2006-11-02
Things seem to be fixed now. I reinstalled Eclipse and switched to the Sun JVM and I can open php files now.

---

### Post by subes on 2006-11-16
I had to remove anything related to gcj with synaptic, because eclipse always used gcj and ignored my Java configuration via:

update-alternatives --config java

To verify for yourself if it loads with gcj, you may run eclipse from a terminal and have a look at the output.

---

### Post by sp00n on 2008-05-17
After experiencing the same problems on Hardy, I have tried all of these, to no avail. How ridiculous, a supposed leading PHP IDE that cannot even open PHP files. Absolutely rubbish.

---

