---
title: "limewire problem"
date: 2005-07-19
forum: General Help
---

### Post by tuxxman on 2005-07-19
hey, i am trying to install limewire but something went wrong
i "alien -d"ed a .rpm i downloaded off of limewire.com and installed the .deb
then i tried to run it, and it told me i needed java, i installed j2re-2.4.2, which after installing limewire again, gave the same error.
someone on my forum channel told me it was the wrong j2re version, and that i need 2.4.1.
they gave me a link and i installed that then tried limewire again, but i get this: 

Starting LimeWire...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/java/j2re1.4.1_01/bin/
Suitable java version found  [/usr/java/j2re1.4.1_01/bin/java = 1.4.1_01]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: /usr/java/j2re1.4.1_01/lib/i386/libfontmanager.so: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1473)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1389)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:832)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.font.NativeFontWrapper.<clinit>(NativeFontWrapper.java:42)
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:125)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:140)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:62)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:72)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:140)
        at java.awt.Toolkit$2.run(Toolkit.java:712)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:703)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:52)
        at com.limegroup.gnutella.gui.Main.main(Main.java:26)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
runLime.sh: line 94: java: command not found


this is severly making me mad.... thanks for the help!

---

### Post by Jet2k5 on 2005-07-19
Don't make your life so hard and complicated.  Just follow the easy GUIDE below,

[http://www.ubuntuguide.org/#limewire](http://www.ubuntuguide.org/#limewire) 

It's much easier and works 99.9% of the time. Just takes a tad bit of searching. :)

---

