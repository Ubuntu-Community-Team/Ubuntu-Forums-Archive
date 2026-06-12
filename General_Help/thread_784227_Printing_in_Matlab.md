---
title: "Printing in Matlab"
date: 2008-05-06
forum: General Help
---

### Post by jorwex on 2008-05-06
Hey all,

I get an "There are no properly configured printers on this system" error. After searching around a bit, I've found this page on Novell's site:

[http://www.novell.com/communities/node/2256/linux+matlab+printing+problem](http://www.novell.com/communities/node/2256/linux+matlab+printing+problem)

They posted a script to remedy the problem. The problem has something to do with java & environmental variables.

```
sh=`echo $SHELL`
sh=${sh:5:4}
if [[ $sh == bash ]] ; then
	echo 'alias matlab="export MATLAB_JAVA=/usr/java/jre1.6.0_01;export JAVA_JVM_VERSION=1.6;matlab"' >> ~/.bashrc
else
	echo 'alias matlab="setenv MATLAB_JAVA /usr/java/jre1.6.0_01;setenv JAVA_JVM_VERSION 1.6;matlab"' >> ~/.cshrc
fi
	echo 'matlab alias set...'
	echo 'load matlab'
```

So I ran that without thinking and then I realized that my paths were different so i changed them to what i thought they were (/usr/lib/jvm/java-6-sun-1.6.0.06/jre) and ran it again and I still get the same error.

I then looked at the script and realized that it was just adding that export MATLAB_JAVA command before launching matlab, so I editted the matlab launching script ($MATLAB$/bin/matlab) and added that line before anyhting else. Now a bunch of scary stuff prints when i try and print in matlab:

```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException: null attribute
	at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
	at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
	at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
	at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
	at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
	at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
	at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
	at com.mathworks.widgets.text.print.PrintSettings.showPrintDialog(PrintSettings.java:665)
	at com.mathworks.mde.cmdwin.XCmdWndView.print(XCmdWndView.java:1644)
	at com.mathworks.mde.cmdwin.CmdWinEditorKit$PrintAction.actionPerformed(CmdWinEditorKit.java:1359)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
	at com.mathworks.mwswing.plaf.MBasicMenuItemUI.doClick(MBasicMenuItemUI.java:1142)
	at com.mathworks.mwswing.plaf.MBasicMenuItemUI$MouseInputHandler.mouseReleased(MBasicMenuItemUI.java:962)
	at java.awt.Component.processMouseEvent(Component.java:6041)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5806)
	at java.awt.Container.processEvent(Container.java:2058)
	at java.awt.Component.dispatchEventImpl(Component.java:4413)
	at java.awt.Container.dispatchEventImpl(Container.java:2116)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
	at java.awt.Container.dispatchEventImpl(Container.java:2102)
	at java.awt.Component.dispatchEvent(Component.java:4243)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
```

while I'm pasting a bunch of code, here's what my matlab script looks like now 

```
#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/ #added tues may 6 2008
export JAVA_JVM_VERSION=1.6
#  Name:
#     matlab    script file for invoking MATLAB
```

alright. thats all. could anyone help me fix my screw ups? could I have to fix anything as a result of running that novell script improperly (like remove any lines I added to any files?). 

Thanks

---

### Post by jorwex on 2008-05-06
SOLUTION!

I figured it out. There's a bug with java & printing. This affects all things java, not just Matlab:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6633656](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6633656)

The solution is outlined here:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/156191/comments/18](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/156191/comments/18)

If I understand correctly, there's a problem with java not having a default choice for the page orientation (landscape, portrait, etc...). So you just have to go to Printing and change default orientation to Portrait or whatever you want in the Job Options tab.

Hooray!

---

