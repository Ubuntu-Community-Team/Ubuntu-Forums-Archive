---
title: "frostwire fails to load..."
date: 2008-03-04
forum: General Help
---

### Post by darkthunderfx on 2008-03-04
For some reason, when attempting to start frostwire it fails to load. I have followed other threads that have similar problems and it looks like I may be getting a different error.

When trying to start it from terminal, this is what I get.

user@user-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_13]
Configuring environment...
Loading FrostWire:

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.font.FontManager$1.run(FontManager.java:178)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(FontManager.java:173)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(SunGraphicsEnvironment.
java:722)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(SunGraphicsEnvir
onment.java:602)
        at sun.java2d.SunGraphicsEnvironment.access$200(SunGraphicsEnvironment.j
ava:58)
        at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:1
74)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:
94)
        at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:164
)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstruct
orAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingC
onstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
        at java.lang.Class.newInstance0(Class.java:350)
        at java.lang.Class.newInstance(Class.java:303)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvi                                                                                                   ronment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:93)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)


Blah, any ideas on making this work?

Thanks again in advance.

Edit: I am running the latest LTS Kubuntu with a 64bit amd.

---

### Post by Metaljaz on 2008-03-04
Read through this wiki and see if it helps. Hope so.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I have frostwire installed and have no problems with it started.
I have this version of java installed:
Java(TM) Plug-in 1.6.0_03-b05

---

