---
title: "java problem (ourtunes app)"
date: 2005-08-26
forum: General Help
---

### Post by holy.sock on 2005-08-26
Hello all! I've been trying to run OurTunes (java applet to browse people's i-tunes music over a network) from a .jar file ($ java -jar OT44.jar).  I just intsalled jre and jdk by d/l'ing the .bin files of sun's website and making and installing a .deb package ($ fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin).  Everything went fine and there didn't seem to be anything wrong.  However when i run $ java -jar OT44.jar i get the following text.
I AM IN CSTC
java.util.NoSuchElementException
   at java.util.Vector.firstElement (Vector.java:401)
   at javax.swing.text.AbstractDocument$BranchElement.getStartOffset (AbstractDocument.java:639)
   at javax.swing.text.FieldView.getPreferredSpan (FieldView.java:74)
   at javax.swing.plaf.basic.BasicTextUI$RootView.getPreferredSpan (BasicTextUI.java:132)
   at javax.swing.plaf.basic.BasicTextUI.getPreferredSize (BasicTextUI.java:358)
   at javax.swing.JComponent.getPreferredSize (JComponent.java:1020)
   at javax.swing.JTextField.getPreferredSize (JTextField.java:275)
   at java.awt.FlowLayout.getSize (FlowLayout.java:334)
   at java.awt.FlowLayout.preferredLayoutSize (FlowLayout.java:252)
   at java.awt.Container.preferredSize (Container.java:626)
   at java.awt.Container.getPreferredSize (Container.java:613)
   at javax.swing.JComponent.getPreferredSize (JComponent.java:1024)
   at javax.swing.BoxLayout.preferredLayoutSize (BoxLayout.java:173)
   at java.awt.Container.preferredSize (Container.java:626)
   at java.awt.Container.getPreferredSize (Container.java:613)
   at javax.swing.JComponent.getPreferredSize (JComponent.java:1024)
   at javax.swing.BoxLayout.preferredLayoutSize (BoxLayout.java:173)
   at java.awt.Container.preferredSize (Container.java:626)
   at java.awt.Container.getPreferredSize (Container.java:613)
   at javax.swing.JComponent.getPreferredSize (JComponent.java:1024)
   at javax.swing.plaf.basic.BasicTabbedPaneUI$TabbedPaneLayout.calculateSize (BasicTabbedPaneUI.java:266)
   at javax.swing.plaf.basic.BasicTabbedPaneUI$TabbedPaneLayout.preferredLayoutSize (BasicTabbedPaneUI.java:708)
   at javax.swing.plaf.basic.BasicTabbedPaneUI.getPreferredSize (BasicTabbedPaneUI.java:1660)
   at javax.swing.JComponent.getPreferredSize (JComponent.java:1020)
   at java.awt.BorderLayout.calcCompSize (BorderLayout.java:655)
   at java.awt.BorderLayout.calcSize (BorderLayout.java:700)
   at java.awt.BorderLayout.preferredLayoutSize (BorderLayout.java:454)
   at java.awt.Container.preferredSize (Container.java:626)
   at java.awt.Container.getPreferredSize (Container.java:613)
   at javax.swing.JComponent.getPreferredSize (JComponent.java:1024)
   at javax.swing.JRootPane$RootLayout.preferredLayoutSize (JRootPane.java:278)
   at java.awt.Container.preferredSize (Container.java:626)
   at java.awt.Container.getPreferredSize (Container.java:613)
   at javax.swing.JComponent.getPreferredSize (JComponent.java:1024)
   at java.awt.BorderLayout.calcCompSize (BorderLayout.java:655)
   at java.awt.BorderLayout.calcSize (BorderLayout.java:700)
   at java.awt.BorderLayout.preferredLayoutSize (BorderLayout.java:454)
   at java.awt.Container.preferredSize (Container.java:626)
   at java.awt.Container.getPreferredSize (Container.java:613)
   at javax.swing.JFrame.getPreferredSize (JFrame.java:91)
   at java.awt.Window.pack (Window.java:243)
   at itunes.client.swing.One2OhMyGod.One2OhMyGod (One2OhMyGod.java:1206)
   at itunes.client.swing.One2OhMyGod.main (One2OhMyGod.java:1243)
   at java.lang.VirtualMachine.invokeMain (VirtualMachine.java)
   at java.lang.VirtualMachine.main (VirtualMachine.java:92)
Is there a java package that I'm missing? I don't think it's and issue w/ ourTunes b/c I've heard of several other people being able to run the app without a problem.  Thanks in advance for any help.

---

