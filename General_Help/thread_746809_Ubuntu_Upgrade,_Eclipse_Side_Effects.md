---
title: "Ubuntu Upgrade, Eclipse Side Effects"
date: 2008-04-05
forum: General Help
---

### Post by zewrestler on 2008-04-05
I recently upgrades my system from Feisty Fawn to Gutsy Gibson.  During the upgade my system crashed. I managed to use apt-get and dkpg to get my system back up and running. However, there have been a few side effects to my eclipse that are weird, and I was hoping to get some help with.  

First, when I open eclipse, Whatever class was open shows the following message:
```
Unable to create this part due to an internal error. Reason for the failure: An exception was thrown during initialization.
java.lang.ClassNotFoundException: org.eclipse.core.runtime.Plugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.core.runtime.Platform.getPlugin(Platform.java:737)
   at org.eclipse.core.internal.preferences.legacy.InitLegacyPreferences.init(InitLegacyPreferences.java:43)
   at org.eclipse.core.internal.preferences.PreferenceServiceRegistryHelper.applyRuntimeDefaults(PreferenceServiceRegistryHelper.java:146)
   at org.eclipse.core.internal.preferences.PreferencesService.applyRuntimeDefaults(PreferencesService.java:337)
   at org.eclipse.core.internal.preferences.DefaultPreferences.applyRuntimeDefaults(DefaultPreferences.java:162)
   at org.eclipse.core.internal.preferences.DefaultPreferences.loadDefaults(DefaultPreferences.java:231)
   at org.eclipse.core.internal.preferences.DefaultPreferences.load(DefaultPreferences.java:227)
   at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java:307)
   at org.eclipse.core.internal.preferences.EclipsePreferences.internalNode(EclipsePreferences.java:543)
   at org.eclipse.core.internal.preferences.EclipsePreferences.node(EclipsePreferences.java:662)
   at org.eclipse.core.internal.preferences.PreferencesService.getNodes(PreferencesService.java:588)
   at org.eclipse.core.internal.preferences.PreferencesService.getString(PreferencesService.java:635)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.getLineDelimiterPreference(TextFileBufferManager.java:645)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.createEmptyDocument(TextFileBufferManager.java:300)
   at org.eclipse.core.internal.filebuffers.ResourceTextFileBuffer.initializeFileBufferContent(ResourceTextFileBuffer.java:268)
   at org.eclipse.core.internal.filebuffers.ResourceFileBuffer.create(ResourceFileBuffer.java:242)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.connect(TextFileBufferManager.java:108)
   at org.eclipse.ui.editors.text.TextFileDocumentProvider.createFileInfo(TextFileDocumentProvider.java:561)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitDocumentProvider.createFileInfo(CompilationUnitDocumentProvider.java:909)
   at org.eclipse.ui.editors.text.TextFileDocumentProvider.connect(TextFileDocumentProvider.java:482)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitDocumentProvider.connect(CompilationUnitDocumentProvider.java:1069)
   at org.eclipse.ui.texteditor.AbstractTextEditor.doSetInput(AbstractTextEditor.java:3063)
   at org.eclipse.ui.texteditor.StatusTextEditor.doSetInput(StatusTextEditor.java:173)
   at org.eclipse.ui.texteditor.AbstractDecoratedTextEditor.doSetInput(AbstractDecoratedTextEditor.java:1512)
   at org.eclipse.jdt.internal.ui.javaeditor.JavaEditor.internalDoSetInput(JavaEditor.java:2371)
   at org.eclipse.jdt.internal.ui.javaeditor.JavaEditor.doSetInput(JavaEditor.java:2344)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitEditor.doSetInput(CompilationUnitEditor.java:1428)
   at org.eclipse.ui.texteditor.AbstractTextEditor$5.run(AbstractTextEditor.java:2396)
   at org.eclipse.jface.operation.ModalContext.runInCurrentThread(ModalContext.java:369)
   at org.eclipse.jface.operation.ModalContext.run(ModalContext.java:313)
   at org.eclipse.jface.window.ApplicationWindow$1.run(ApplicationWindow.java:763)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.jface.window.ApplicationWindow.run(ApplicationWindow.java:760)
   at org.eclipse.ui.internal.WorkbenchWindow.run(WorkbenchWindow.java:2283)
   at org.eclipse.ui.texteditor.AbstractTextEditor.internalInit(AbstractTextEditor.java:2414)
   at org.eclipse.ui.texteditor.AbstractTextEditor.init(AbstractTextEditor.java:2441)
   at org.eclipse.ui.internal.EditorManager.createSite(EditorManager.java:842)
   at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:583)
   at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:372)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
   at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:263)
   at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1474)
   at org.eclipse.ui.internal.EditorManager$5.run(EditorManager.java:1008)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.core.runtime.Platform.run(Platform.java:858)
   at org.eclipse.ui.internal.EditorManager.restoreState(EditorManager.java:1003)
   at org.eclipse.ui.internal.WorkbenchPage.restoreState(WorkbenchPage.java:2843)
   at org.eclipse.ui.internal.WorkbenchWindow.restoreState(WorkbenchWindow.java:1936)
   at org.eclipse.ui.internal.Workbench.doRestoreState(Workbench.java:2873)
   at org.eclipse.ui.internal.Workbench.access$14(Workbench.java:2821)
   at org.eclipse.ui.internal.Workbench$19.run(Workbench.java:1697)
   at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)
   at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1695)
   at org.eclipse.ui.internal.Workbench.access$12(Workbench.java:1666)
   at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1545)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1489)
   at org.eclipse.ui.internal.WorkbenchConfigurer.restoreState(WorkbenchConfigurer.java:183)
   at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:702)
   at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)
   at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```

----------------------------------------
This doesn't bother me that much, considering all I have to do to get around this is to close the current class and reopen it.  However, I have had issues with some java classes that worked before not being able to be resolved now.  

For instance, when i import the scanner class, I get the message "java.util.Scanner" cannot be resolved.

Does anyone have any suggestion of how I can fix this problem?

---

### Post by zewrestler on 2008-04-06
So it turns out that the upgrade changed the default version of java that I had working on my Eclipse settings without alerting me to the change.  

For some reason, the default on my eclipse settings was changed to java-gcj.

I changed it to java-6-sun and the changes took effect and the system was able to finally resolve the java.util.Scanner class and the others that it had problems computing. 

However, the other error that appears when I open the screen still occurs.  Any suggestions of how to fix it?

---

