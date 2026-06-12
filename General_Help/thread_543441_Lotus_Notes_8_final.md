---
title: "Lotus Notes 8 final"
date: 2007-09-05
forum: General Help
---

### Post by Cloud79 on 2007-09-05
Theres no longer any need to install notes 7 with wine (if u dont need the administrator client or designer)

I have tested the client with Feisty and Gutsy.

install with sudo setup.sh

i then changed permission on /etc/lotus, /home/%user%/lotus and /opt/ibm to be owned by my user.

Works like a charm with one exception on my work computer, it doesn't show html mail (but works on my computer at home). I can't find out why. This is the error message i recieive.

Any suggestions for a fix?

```
Unable to create view: Device is disposed

org.eclipse.swt.SWTException: Device is disposed
	at org.eclipse.swt.SWT.error(SWT.java:3563)
	at org.eclipse.swt.SWT.error(SWT.java:3481)
	at org.eclipse.swt.SWT.error(SWT.java:3452)
	at com.ibm.rcp.ui.internal.browser.BrowserControl$EmbeddedBrowserImpl.addCloseWindowListener(BrowserControl.java:3325)
	at com.ibm.rcp.ui.internal.browser.launcher.BrowserInstanceListener.<init>(BrowserInstanceListener.java:62)
	at com.ibm.rcp.ui.internal.browser.launcher.APPBrowserView.createPartControl(APPBrowserView.java:139)
	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:332)
	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:290)
	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:525)
	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:140)
	at com.ibm.rcp.ui.internal.presentations.StandAloneStackPresentation.selectPart(StandAloneStackPresentation.java:292)
	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1144)
	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1097)
	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1311)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:601)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:532)
	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:562)
	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:244)
	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:815)
	at org.eclipse.ui.internal.WorkbenchPage.setPerspective(WorkbenchPage.java:3269)
	at org.eclipse.ui.internal.WorkbenchPage.busySetPerspective(WorkbenchPage.java:956)
	at org.eclipse.ui.internal.WorkbenchPage.access$12(WorkbenchPage.java:940)
	at org.eclipse.ui.internal.WorkbenchPage$12.run(WorkbenchPage.java:3368)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchPage.setPerspective(WorkbenchPage.java:3366)
	at com.ibm.rcp.platform.personality.internal.window.DynamicPerspective.open(DynamicPerspective.java:87)
	at com.ibm.rcp.platform.personality.internal.window.SwitcherWindowHelper.show(SwitcherWindowHelper.java:239)
	at com.ibm.rcp.platform.personality.widgets.TabbedPerspectiveSwitcher.show(TabbedPerspectiveSwitcher.java:1162)
	at com.ibm.rcp.ui.internal.browser.launcher.BrowserLauncherImpl.run(BrowserLauncherImpl.java:128)
	at com.ibm.rcp.ui.internal.browser.launcher.BrowserLauncherImpl.run(BrowserLauncherImpl.java:58)
	at com.ibm.rcp.ui.browser.launcher.BrowserLauncher.launchURLasDefault(BrowserLauncher.java:56)
	at com.ibm.workplace.noteswc.NotesURLHandler.launchGenericURL(NotesURLHandler.java:185)
	at com.ibm.workplace.noteswc.NotesListener$17.run(NotesListener.java:1131)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3296)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2974)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1931)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1895)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:423)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at com.ibm.rcp.personality.framework.internal.RCPApplication.run(RCPApplication.java:72)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:64)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:615)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at com.ibm.rcp.core.internal.launcher.Main.startLaunch(Main.java:895)
	at com.ibm.rcp.core.internal.launcher.Main.main(Main.java:1313)

```

---

### Post by chouf on 2007-10-19
I found [the following post]("http://www.glump.net/dokuwiki/howto/notes_8_on_ubuntu") which explains in details how to install Lotus Notes v8.0 on Ubuntu. I followed this guide and it worked like a charm.

I also created a small install guide (enclosed in the tar.gz file attached) based on the guide mentioned above but giving more detailed newbish instructions (I'm a newbie so that's why I've created this guide - to be able to reinstall Lotus Notes if needed ;-) I would never remember all this)

---

### Post by Aito on 2007-12-04
Thumbs up Chouf !!

I was stuck with the 'windows without button' issue but your guide was complete enough to even talk about this point !!

So thank again :)

Best

Aito

---

