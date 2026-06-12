---
title: "Java problems (running weka)"
date: 2006-10-30
forum: General Help
---

### Post by viraptor on 2006-10-30
Hello
After upgrading to edgy I get this, when trying to use weka (trace from 3.5.3, but any other version does this also):

```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        weka.gui.explorer.PreprocessPanel.addPropertyChangeListener(Unknown Source)
        javax.swing.plaf.synth.SynthPanelUI.installListeners(SynthPanelUI.java:49)
        javax.swing.plaf.synth.SynthPanelUI.installUI(SynthPanelUI.java:38)
        javax.swing.JComponent.setUI(JComponent.java:652)
        javax.swing.JPanel.setUI(JPanel.java:131)
        javax.swing.JPanel.updateUI(JPanel.java:104)
        javax.swing.JPanel.<init>(JPanel.java:64)
        javax.swing.JPanel.<init>(JPanel.java:87)
        javax.swing.JPanel.<init>(JPanel.java:95)
        weka.gui.explorer.PreprocessPanel.<init>(Unknown Source)
        weka.gui.explorer.Explorer.<init>(Unknown Source)
        weka.gui.GUIChooser$2.actionPerformed(Unknown Source)
        java.awt.Button.processActionEvent(Button.java:388)
        java.awt.Button.processEvent(Button.java:356)
        java.awt.Component.dispatchEventImpl(Component.java:3955)
        java.awt.Component.dispatchEvent(Component.java:3803)
        java.awt.EventQueue.dispatchEvent(EventQueue.java:463)
        java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:242)
        java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:163)
        java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:157)
        java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:149)
        java.awt.EventDispatchThread.run(EventDispatchThread.java:110)

        at weka.gui.explorer.PreprocessPanel.addPropertyChangeListener(Unknown Source)
        at javax.swing.plaf.synth.SynthPanelUI.installListeners(SynthPanelUI.java:49)
        at javax.swing.plaf.synth.SynthPanelUI.installUI(SynthPanelUI.java:38)
        at javax.swing.JComponent.setUI(JComponent.java:652)
        at javax.swing.JPanel.setUI(JPanel.java:131)
        at javax.swing.JPanel.updateUI(JPanel.java:104)
        at javax.swing.JPanel.<init>(JPanel.java:64)
        at javax.swing.JPanel.<init>(JPanel.java:87)
        at javax.swing.JPanel.<init>(JPanel.java:95)
        at weka.gui.explorer.PreprocessPanel.<init>(Unknown Source)
        at weka.gui.explorer.Explorer.<init>(Unknown Source)
        at weka.gui.GUIChooser$2.actionPerformed(Unknown Source)
        at java.awt.Button.processActionEvent(Button.java:388)
        at java.awt.Button.processEvent(Button.java:356)
        at java.awt.Component.dispatchEventImpl(Component.java:3955)
        at java.awt.Component.dispatchEvent(Component.java:3803)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:463)
        at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:242)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:163)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:157)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:149)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:110)
```

I'm using sun-java. Bug is already in launchpad for that package. Anyone else seen it? Maybe someone knows a workaround.

It worked under dapper and runs clean on any other system, that I checked.

---

### Post by bigodines on 2006-11-12
I've had the same problem with Dapper.

Solved creating a file named: LookAndFeel.pros

with this in it:

> Theme=javax.swing.plaf.metal.MetalLookAndFeel

hope this helps for future users with this problem.

---

### Post by viraptor on 2006-11-12
How can I change that file in weka.jar?
I've unpacked it, changed weka/gui/LookAndFeel.prop, but now jar throws:
```
adding: weka/java.util.zip.ZipException: duplicate entry: weka/
        at java.util.zip.ZipOutputStream.putNextEntry(ZipOutputStream.java:163)
        at java.util.jar.JarOutputStream.putNextEntry(JarOutputStream.java:90)
        at sun.tools.jar.Main.addFile(Main.java:608)
        at sun.tools.jar.Main.create(Main.java:412)
        at sun.tools.jar.Main.run(Main.java:142)
        at sun.tools.jar.Main.main(Main.java:903)
```
when I try to pack it again.

---

