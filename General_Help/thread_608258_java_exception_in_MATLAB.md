---
title: "java exception in MATLAB"
date: 2007-11-09
forum: General Help
---

### Post by sippyCUP on 2007-11-09
I use Ubuntu 7.10 and MATLAB 7.4 (R2007A). MATLAB uses java, my JVM is java-6-sun-1.6.0.03. For some reason when I try to print anything (figures or m-files) I get a nasty java exception error. I can print using matlab commands (print -f1 or something) but that is cumbersome if I want to customize how the object is printed. I don't really know where to start here, any ideas? Here is the error.

java.lang.NullPointerException: null attribute
	at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
	at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
	at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
	at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
	at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
	at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
	at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
	at com.mathworks.page.export.printdlg.Printdlg.setVisible(Printdlg.java:470)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.mathworks.jmi.AWTUtilities$Invoker$2.runWithOutput(AWTUtilities.java:135)
	at com.mathworks.jmi.AWTUtilities$Invoker$1.run(AWTUtilities.java:103)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)

---

### Post by Saverio on 2007-11-13
I had the same problem, I solved using Java 1.5 (which is the version given as a requirement by Mathworks).

Moreover, do a 
export AWT_TOOLKIT=MToolkit

I had an extra problem of huge fonts, but you can set them in the Preferences.

Now everything seems ok, a part from the fact that
1. when I type TAB for auto completion, the list of possibilities comes out in the background, I have to alt-tab to see it
2. in simulink double click doesn't work, I have to click and after a small delay the object get focus and I can press Enter

Let me know if you have the same problems.
Ciao!
Saverio

---

### Post by syxbit on 2008-02-04
i'm still having that same printing error
exporting AWT_TOOLKIT doesn't work, as i can't even load up matlab if i do that

---

### Post by kbless7 on 2008-02-05
The thread at this link addresses java issues in matlab.

[http://ubuntuforums.org/showthread.php?t=672625&page=3&highlight=kbless7](http://ubuntuforums.org/showthread.php?t=672625&page=3&highlight=kbless7)

---

