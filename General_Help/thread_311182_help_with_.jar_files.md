---
title: "help with .jar files?"
date: 2006-12-02
forum: General Help
---

### Post by andyanderso on 2006-12-02
Hi,

I don't know much about java or how to run .jar files.

I do have a .jar program that I need to run for work and I would really love to be able to run it on my ubuntu machine.

Can anyone help me learn how to execute a .jar program on my machine?

here is my java version ( i would like to run java 1.5.x but i can't figure out how to install it.)
> andy@hermes:~/Desktop$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
andy@hermes:~/Desktop$ 


I tried this:
> andy@hermes:~/Desktop$ sudo java -jar PC-Pilot.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at AviFrame.<init>(AviFrame.java:10)
   at AviFrame.main(AviFrame.java:42)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...6 more
andy@hermes:~/Desktop$ 


please help.

andy

---

### Post by gutek on 2006-12-14
well i think you need to install this package: libgcj7-awt

Gutek

---

### Post by meng on 2006-12-14
Search the wiki for "java" if you wish to install sun's java.

---

### Post by davim on 2007-01-11
to run a jar file type in a terminal:

java -jar jarfile.jar

---

### Post by renatosilva on 2007-01-11
Andy how did you installed Java. Once i did it on Ubuntu 6.10 at my work. It worked fine and the .jar extension was automatically associated in the GNOME. I ran an AWT aplication ([this]("http://br.geocities.com/renato3110/projects/jaca/jaca.jar")) with no problem.

I used Synaptic and just marked sun-java5-sdk for installing, and all the dependencies was marked as well.

---

### Post by renatosilva on 2007-01-11
Just now I've seen you're using GNU software!! Install  the Sun JRE/JDK as I've said.

---

