---
title: "swt-gtk error"
date: 2008-06-10
forum: General Help
---

### Post by hrafninn on 2008-06-10
I am running Ubuntu 7.10 and trying to run a Java application which uses SWT (Standard Widget Toolkit).

When I try to run the program with
java -jar ctagger_linux32.jar

I get the error message:
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-gtk-3349 or swt-gtk in swt.library.path, java.library.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
        at is.ru.ctagger.UserInterface.<init>(UserInterface.java:89)
        at is.ru.ctagger.CombinedTagging.main(CombinedTagging.java:34)

I tried:
java -Djava.library.path=/usr/java/swt -jar ctagger_linux32.jar

where ls -las /usr/java/swt gives:
 4 drwxrwxrwx 3 root  root     4096 2008-06-09 14:34 .
   4 drwxr-xr-x 7 root  root     4096 2008-06-09 14:32 ..
   4 drwxr-xr-x 2 hrafn hrafn    4096 2008-02-21 21:54 about_files
  16 -rw-r--r-- 1 hrafn hrafn   13852 2008-02-21 21:54 about.html
   4 -rw-r--r-- 1 hrafn hrafn     589 2008-02-21 21:54 .classpath
   4 -rw-r--r-- 1 hrafn hrafn     373 2008-02-21 21:54 .project
1664 -rw-r--r-- 1 hrafn hrafn 1696547 2008-02-21 21:54 src.zip
1708 -rw-r--r-- 1 hrafn hrafn 1740866 2008-02-21 21:54 swt-debug.jar
1224 -rw-r--r-- 1 hrafn hrafn 1246002 2008-02-21 21:54 swt.jar

But still get the same message.


I also tried to install:
sudo apt-get install libgtk-java

but without success.

Does anyone know what I need to do to make this run?  Do I need to install Eclipse?  I'm not developing the program, I just want to run it.

---

