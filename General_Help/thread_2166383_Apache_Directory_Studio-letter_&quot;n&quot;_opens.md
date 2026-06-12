---
title: "Apache Directory Studio-letter &quot;n&quot; opens an Assistent (Menu File-&gt;Neu,shortcut CTR+N)"
date: 2013-08-09
forum: General Help
---

### Post by Monika_Ondrejova on 2013-08-09
Hello, 

I bought a neu Computer and installed  in Ubuntu 12.04  ApacheDirectoryStudio-linux-x86_64-2.0.0.v20130308 (release from 08.03.2013). Since that, each time wenn I write som Value  consisting letter "n" openes the Assistent, that you can start from Menu File->Neu. Its shortcut is CTRL+N.

My solution for this ist just to write the word with letter "n" in some editor outside Apache Directory Studio and  copy-paste it into Apache Directory Studio. It boders me. 


I thought it is a bug. But yesterday I downloaded  ApacheDirectoryStudio-linux-x86_64-2.0.0.v20130628.tar.gz (release from 28.06.2013). And decompressed it to home directory.
The old .ApacheDirectoryStudio  - I renamed.
I started the newer ApacheDirectoryStudio. It created a new directory  .ApacheDirectoryStudio.
 
But the problem with letter "n" is still there, Wenn I write letter "n" in ~/ApacheDirectoryStudio/.metadata/.log  will be generated this Rows: 

!ENTRY org.eclipse.ui 4 0 2013-08-09 08:44:36.633
!MESSAGE Unhandled event loop exception
!STACK 0
org.eclipse.swt.SWTException: Failed to execute runnable (java.lang.NullPointerException)
    at org.eclipse.swt.SWT.error(SWT.java:4361)
    at org.eclipse.swt.SWT.error(SWT.java:4276)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:138)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3529)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3182)
    at org.eclipse.jface.window.Window.runEventLoop(Window.java:825)
    at org.eclipse.jface.window.Window.open(Window.java:801)
    at org.eclipse.ui.internal.handlers.WizardHandler$New.executeHandler(WizardHandler.java:259)
    at org.eclipse.ui.internal.handlers.WizardHandler.execute(WizardHandler.java:279)
    at org.eclipse.ui.internal.handlers.HandlerProxy.execute(HandlerProxy.java:290)
    at org.eclipse.core.commands.Command.executeWithChecks(Command.java:499)
    at org.eclipse.core.commands.ParameterizedCommand.executeWithChecks(ParameterizedCommand.java:508)
    at org.eclipse.ui.internal.handlers.HandlerService.executeCommand(HandlerService.java:169)
    at org.eclipse.ui.internal.handlers.SlaveHandlerService.executeCommand(SlaveHandlerService.java:241)
    at org.eclipse.ui.internal.actions.CommandAction.runWithEvent(CommandAction.java:157)
    at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:584)
    at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:501)
    at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:411)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1276)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3554)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3179)
    at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2701)
    at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2665)
    at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2499)
    at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:679)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:668)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
    at org.apache.directory.studio.Application.start(Application.java:51)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:353)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:180)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
Caused by: java.lang.NullPointerException
    at org.apache.directory.studio.ldapbrowser.ui.editors.entry.EntryEditorOutlinePage.refresh(EntryEditorOutlinePage.java:232)
    at org.apache.directory.studio.ldapbrowser.ui.editors.entry.EntryEditorUniversalListener.entryUpdated(EntryEditorUniversalListener.java:193)
    at org.apache.directory.studio.ldapbrowser.core.events.EventRegistry$4$1.run(EventRegistry.java:237)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
    ... 40 more


!ENTRY org.eclipse.jface 4 0 2013-08-09 08:44:36.692
!MESSAGE Unhandled event loop exception during blocked modal context.
!STACK 0
org.eclipse.swt.SWTException: Failed to execute runnable (java.lang.NullPointerException)
    at org.eclipse.swt.SWT.error(SWT.java:4361)
    at org.eclipse.swt.SWT.error(SWT.java:4276)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:138)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3529)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3182)
    at org.eclipse.jface.operation.ModalContext$ModalContextThread.block(ModalContext.java:173)
    at org.eclipse.jface.operation.ModalContext.run(ModalContext.java:388)
    at org.eclipse.jface.dialogs.ProgressMonitorDialog.run(ProgressMonitorDialog.java:507)
    at org.eclipse.ui.internal.progress.ProgressMonitorJobsDialog.run(ProgressMonitorJobsDialog.java:275)
    at org.eclipse.ui.internal.progress.ProgressManager$5.run(ProgressManager.java:960)
    at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
    at org.eclipse.ui.internal.progress.ProgressManager.busyCursorWhile(ProgressManager.java:995)
    at org.eclipse.ui.internal.progress.ProgressManager.busyCursorWhile(ProgressManager.java:970)
    at org.eclipse.ui.internal.progress.ProgressManager.run(ProgressManager.java:1166)
    at org.apache.directory.studio.connection.ui.RunnableContextRunner.execute(RunnableContextRunner.java:140)
    at org.apache.directory.studio.entryeditors.EntryEditorManager$3.entryUpdated(EntryEditorManager.java:420)
    at org.apache.directory.studio.ldapbrowser.core.events.EventRegistry$4$1.run(EventRegistry.java:237)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3529)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3182)
    at org.eclipse.jface.window.Window.runEventLoop(Window.java:825)
    at org.eclipse.jface.window.Window.open(Window.java:801)
    at org.eclipse.ui.internal.handlers.WizardHandler$New.executeHandler(WizardHandler.java:259)
    at org.eclipse.ui.internal.handlers.WizardHandler.execute(WizardHandler.java:279)
    at org.eclipse.ui.internal.handlers.HandlerProxy.execute(HandlerProxy.java:290)
    at org.eclipse.core.commands.Command.executeWithChecks(Command.java:499)
    at org.eclipse.core.commands.ParameterizedCommand.executeWithChecks(ParameterizedCommand.java:508)
    at org.eclipse.ui.internal.handlers.HandlerService.executeCommand(HandlerService.java:169)
    at org.eclipse.ui.internal.handlers.SlaveHandlerService.executeCommand(SlaveHandlerService.java:241)
    at org.eclipse.ui.internal.actions.CommandAction.runWithEvent(CommandAction.java:157)
    at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:584)
    at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:501)
    at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:411)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1276)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3554)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3179)
    at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2701)
    at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2665)
    at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2499)
    at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:679)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:668)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
    at org.apache.directory.studio.Application.start(Application.java:51)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:353)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:180)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
Caused by: java.lang.NullPointerException
    at org.apache.directory.studio.ldapbrowser.ui.editors.entry.EntryEditorOutlinePage.refresh(EntryEditorOutlinePage.java:232)
    at org.apache.directory.studio.ldapbrowser.ui.editors.entry.EntryEditorUniversalListener.entryUpdated(EntryEditorUniversalListener.java:193)
    at org.apache.directory.studio.ldapbrowser.core.events.EventRegistry$4$1.run(EventRegistry.java:237)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
    ... 56 more


!ENTRY org.eclipse.ui 4 0 2013-08-09 08:44:36.785
!MESSAGE Unhandled event loop exception
!STACK 0
org.eclipse.swt.SWTException: Failed to execute runnable (java.lang.NullPointerException)
    at org.eclipse.swt.SWT.error(SWT.java:4361)
    at org.eclipse.swt.SWT.error(SWT.java:4276)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:138)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3529)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3182)
    at org.eclipse.jface.window.Window.runEventLoop(Window.java:825)
    at org.eclipse.jface.window.Window.open(Window.java:801)
    at org.eclipse.ui.internal.handlers.WizardHandler$New.executeHandler(WizardHandler.java:259)
    at org.eclipse.ui.internal.handlers.WizardHandler.execute(WizardHandler.java:279)
    at org.eclipse.ui.internal.handlers.HandlerProxy.execute(HandlerProxy.java:290)
    at org.eclipse.core.commands.Command.executeWithChecks(Command.java:499)
    at org.eclipse.core.commands.ParameterizedCommand.executeWithChecks(ParameterizedCommand.java:508)
    at org.eclipse.ui.internal.handlers.HandlerService.executeCommand(HandlerService.java:169)
    at org.eclipse.ui.internal.handlers.SlaveHandlerService.executeCommand(SlaveHandlerService.java:241)
    at org.eclipse.ui.internal.actions.CommandAction.runWithEvent(CommandAction.java:157)
    at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:584)
    at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:501)
    at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:411)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1276)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3554)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3179)
    at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2701)
    at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2665)
    at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2499)
    at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:679)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:668)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
    at org.apache.directory.studio.Application.start(Application.java:51)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:353)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:180)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
Caused by: java.lang.NullPointerException
    at org.apache.directory.studio.ldapbrowser.ui.editors.entry.EntryEditorOutlinePage.refresh(EntryEditorOutlinePage.java:232)
    at org.apache.directory.studio.ldapbrowser.ui.editors.entry.EntryEditorUniversalListener.entryUpdated(EntryEditorUniversalListener.java:193)
    at org.apache.directory.studio.ldapbrowser.core.events.EventRegistry$4$1.run(EventRegistry.java:237)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
    ... 40 more



What schould I change? Some Parameters in Ubuntu?

---

