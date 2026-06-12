---
title: "error writing graphics file"
date: 2013-03-01
forum: General Help
---

### Post by triticale on 2013-03-01
A tree file was generated through FigTree, a java program. I tried to save the file to a graphics format, like jpg, png. I used to use my laptop, which worked fine. But when I turned to my desktop, and it didn't work. 

The error message is : Error writing graphics file. I don't know whether or not there are libs lost.

---

### Post by QIII on 2013-03-01
*Moved to **General Help***

Your question is very vague.  You might consider giving a bit more detail.

Cheers!  Good luck.

---

### Post by triticale on 2013-03-01
I was using FigTree, a program commonly used in biology field for drawing phylogenetic tree based on some numerical data. The image is shown like this:

[http://openwetware.org/wiki/Image:Screenshot1.png](http://openwetware.org/wiki/Image:Screenshot1.png)

Then I click File > Export Graphic...  It shows like this:
 
[http://openwetware.org/wiki/Image:Screenshot2.png](http://openwetware.org/wiki/Image:Screenshot2.png)

 I click pull-down menu. Usually I can choose what format I want, like jpg, or png here. But here the pull-down menu is blank!

I click OK to save, and the error message is like this:

[http://openwetware.org/wiki/Image:Screenshot3.png](http://openwetware.org/wiki/Image:Screenshot3.png)
 
I click "Details..." here, and it showed like this:

[http://openwetware.org/wiki/Image:Screenshot4.png](http://openwetware.org/wiki/Image:Screenshot4.png)

I don't know whether there is a problem with my Ubuntu 10.04 system. Thank you. 


> **triticale said:**
> A tree file was generated through FigTree, a java program. I tried to save the file to a graphics format, like jpg, png. I used to use my laptop, which worked fine. But when I turned to my desktop, and it didn't work. 

The error message is : Error writing graphics file. I don't know whether or not there are libs lost.

---

### Post by triticale on 2013-03-03
New finding! When I [COLOR=#000000] I go to "File > Export Graphic..." , there is error message in the black box where I type commands. It's like this:

[/COLOR]Exception in thread "AWT-EventQueue-0" java.lang.ExceptionInInitializerError
	at org.freehep.graphicsio.gif.GIFImageWriteParam.<init>(GIFImageWriteParam.java:28)
	at org.freehep.graphicsio.gif.GIFImageWriter.getDefaultWriteParam(GIFImageWriter.java:73)
	at org.freehep.graphicsio.exportchooser.ImageExportFileType.<init>(ImageExportFileType.java:71)
	at org.freehep.graphicsio.gif.GIFExportFileType.<init>(GIFExportFileType.java:42)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:374)
	at java.lang.Class.newInstance(Class.java:327)
	at org.freehep.util.Service.providers(Service.java:71)
	at org.freehep.util.export.ExportFileTypeRegistry.addApplicationClasspathExportFileTypes(ExportFileTypeRegistry.java:118)
	at org.freehep.util.export.ExportFileTypeRegistry.getDefaultInstance(ExportFileTypeRegistry.java:50)
	at org.freehep.util.export.ExportFileType.getExportFileTypes(ExportFileType.java:181)
	at org.freehep.util.export.ExportFileType.getExportFileTypes(ExportFileType.java:173)
	at org.freehep.util.export.ExportDialog.addAllExportFileTypes(ExportDialog.java:64)
	at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:130)
	at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:90)
	at org.freehep.util.export.ExportDialog.<init>(ExportDialog.java:82)
	at figtree.application.FigTreeFrame.doExportGraphic(Unknown Source)
	at figtree.application.FigTreeFrame$22.actionPerformed(Unknown Source)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:2012)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2335)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:404)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:259)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:374)
	at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:829)
	at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:873)
	at java.awt.Component.processMouseEvent(Component.java:6288)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
	at java.awt.Component.processEvent(Component.java:6053)
	at java.awt.Container.processEvent(Container.java:2045)
	at java.awt.Component.dispatchEventImpl(Component.java:4649)
	at java.awt.Container.dispatchEventImpl(Container.java:2103)
	at java.awt.Component.dispatchEvent(Component.java:4475)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4633)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4297)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4227)
	at java.awt.Container.dispatchEventImpl(Container.java:2089)
	at java.awt.Window.dispatchEventImpl(Window.java:2587)
	at java.awt.Component.dispatchEvent(Component.java:4475)
	at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:675)
	at java.awt.EventQueue.access$300(EventQueue.java:96)
	at java.awt.EventQueue$2.run(EventQueue.java:634)
	at java.awt.EventQueue$2.run(EventQueue.java:632)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
	at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:116)
	at java.awt.EventQueue$3.run(EventQueue.java:648)
	at java.awt.EventQueue$3.run(EventQueue.java:646)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:645)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
Caused by: java.lang.NullPointerException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.freehep.graphics2d.PixelGraphics2D.<clinit>(PixelGraphics2D.java:101)
	... 59 more

---

### Post by triticale on 2013-03-04
Please help me!

---

### Post by Impavidus on 2013-03-05
I don't think there are many people here having experience with this software.

You could open synaptics or the software centre and search for java image export libraries. If they haven't been installed installing them may help. Else you can try contacting other people who use this software (you seem to know them) or even the developers of this software. They may be able to tell you what java libraries you need and how they got it working -- if any of them use linux. I don't know how prevalent linux is in biology circles.

---

