---
title: "Installing ImageJ"
date: 2008-05-03
forum: General Help
---

### Post by Rchen on 2008-05-03
Hello guys
I am trying to install ImageJ on a compaq nx6325 machine (edubuntu 7.10), but after inserting the run command I keep getting this:

Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/chen/Applications/ImageJ/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
at java.lang.ClassLoader$NativeLibrary.load(Native Method)
at java.lang.ClassLoader.loadLibrary0(ClassLoader.jav a:1751)
at java.lang.ClassLoader.loadLibrary(ClassLoader.java :1647)
at java.lang.Runtime.load0(Runtime.java:770)
at java.lang.System.load(System.java:1005)
at java.lang.ClassLoader$NativeLibrary.load(Native Method)
at java.lang.ClassLoader.loadLibrary0(ClassLoader.jav a:1751)
at java.lang.ClassLoader.loadLibrary(ClassLoader.java :166
at java.lang.Runtime.loadLibrary0(Runtime.java:823)
at java.lang.System.loadLibrary(System.java:1030)
at sun.security.action.LoadLibraryAction.run(LoadLibr aryAction.java:50)
at java.security.AccessController.doPrivileged(Native Method)
at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoa der.java:3
at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
at java.awt.Component.<clinit>(Component.java:552)

locate libXext.so.6
gives:

/usr/lib/libXext.so.6
/usr/lib/libXext.so.6.0
/usr/lib/libXext.so.6.4.0

any ideas? :(

---

### Post by JangMunho on 2008-05-03
Try sudo apt-get install libxext6

---

### Post by Rchen on 2008-05-03
thanks JangMunho
I did it but apparently it is already installed and I keep getting the same error.
[COLOR="Blue"]
libxext6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libmagick9 libopenal0a libglew1.4 libalut0[/COLOR]

---

### Post by Rchen on 2008-05-03
OK, 
so the problem was the the ia32 files, and the lib32gcc files. After downloading them, the installation just worked fine.

Chen

---

