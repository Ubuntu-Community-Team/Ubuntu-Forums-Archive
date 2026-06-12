---
title: "problem installing a plugin for eclipse"
date: 2007-06-03
forum: General Help
---

### Post by drorl on 2007-06-03
hi.
i have the latest version of eclipse installed on my laptop and i try to install a UML plugin from omondo.

it doesn't seem to work and the problem is not related to the plugin software itself.
looks like missing components of java (i tried to install it again but it didn't help)

when trying to install with this command (as suggested in their FAQ page):
drorl@drorl-laptop:~/Desktop$ sudo java -jar eclipseUML_E320_freeEdition_2.1.0.20061006.jar

i get the following output:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.Font.tk(libgcj.so.70)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.70)
   at java.awt.Font.<init>(libgcj.so.70)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.70)
   at javax.swing.plaf.metal.DefaultMetalTheme .<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.70)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.70)
   at javax.swing.UIManager.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at com.izforge.izpack.installer.GUIInstaller.loadLookAndFeel (GUIInstaller.java:224)
   at com.izforge.izpack.installer.GUIInstaller.<init>(GUIInstaller.java:101)
   at java.lang.Class.newInstance(libgcj.so.70)
   at com.izforge.izpack.installer.Installer.main(Installer.java :47)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary (libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName (libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...15 more

any one has an idea what is it? what is missing and where to get it from?
thanks
dror

---

