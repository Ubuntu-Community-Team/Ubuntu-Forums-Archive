---
title: "Sun Download Manager not working"
date: 2007-03-27
forum: General Help
---

### Post by tushar.novice on 2007-03-27
I use Ubuntu 6.06

I want to download the Solaris10 OS.
I want to do it using Sun Download Manager.
For this, I installed latest (I think it was 5.0) Java Runtime Environment as was given in the ubuntu online help.
Still, when I try to use SDM, nothing happens.
When I click on its icon,  theres complete silence and typing it out in the terminal yields nothing except this gibberish

[I]Sun (TM) Download Manager 1.3
Copyright (c) 2001-2004 by Sun Microsystems, Inc.
All rights reserved.
Starting Java interpreter...
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.sun.sdm.SunDownloadManager.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...11 more[/I]


Do you guys have any clue whats happening????

---

### Post by Ramses de Norre on 2007-03-27
Did you install java 5 from the repo? If so, do this: ```
sudo update-java-alternatives -s java-1.5.0-sun
```
If you got java from some other source, you can run the same command with the -l flag to find whether ubuntu sees your manual install, if it doesn't you'll need to link all java stuff from /usr/bin/ to your jre manually or set the JAVA_HOME option in your ~/.bashrc file.

---

