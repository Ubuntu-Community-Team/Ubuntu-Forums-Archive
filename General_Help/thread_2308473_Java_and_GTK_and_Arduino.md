---
title: "Java and GTK and Arduino"
date: 2016-01-03
forum: General Help
---

### Post by koszyk.spamowy on 2016-01-03
Hi, 

I have reinstalled system from Xubuntu 14.04 32 bit to 15.10 64bit and I'm trying to run Arduino and I have got:

tristan@minilenek:~/Pulpit/arduino-1.6.7$ ./arduino
Picked up JAVA_TOOL_OPTIONS: 
java.lang.Error: Cannot load com.sun.java.swing.plaf.gtk.GTKLookAndFeel
        at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1351)
        at javax.swing.UIManager.initialize(UIManager.java:1459)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1426)
        at javax.swing.UIManager.getLookAndFeel(UIManager.java:492)
        at processing.app.linux.GTKLookAndFeelFixer.installGtkPopupBugWorkaround(GTKLookAndFeelFixer.java:79)
        at processing.app.linux.Platform.setLookAndFeel(Platform.java:48)
        at processing.app.Base.guardedMain(Base.java:213)
        at processing.app.Base.main(Base.java:136)


I have installed oracle-java8-installer but there is the same error. What should I do?

---

