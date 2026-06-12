---
title: "Problem running Java application"
date: 2006-10-22
forum: General Help
---

### Post by tesseract420 on 2006-10-22
Hi,

I've installed java but I can't get a program to run. Here's the error message I get:

desktop:~/udiskfolder/linuxdarkroom$ java JDarkroom.jar
Exception in thread "main" java.lang.NoClassDefFoundError: JDarkroom.jar
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: JDarkroom.jar not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)


I'm guessing something's missing? The application runs fine on other platforms.

Any ideas?

---

### Post by bukwirm on 2006-10-22
The gcj virtual machine doesn't support all the graphical classes, so you may need to install Sun Java.

If you installed the Sun packages already, run "sudo update-aternatives --config java" and select the correct option to make sure you're using them.

---

### Post by shaviro on 2007-10-24
I have also had problems with this Java app (JDarkRoom.jar) since upgrading to Gutsy.
Under Feisty, JDarkRoom.jar worked with Sun Java 1.6. But when I try to run it in Gutsy, I get:
> 
Not setting native look & feel.
Full-screen mode not supported.  Please consider upgrading your version of Java, or using JDarkRoom on a device that supports full-screen mode.


I have checked that the correct version of Java is inded running.

---

### Post by cytg on 2007-10-24
noob :)

java -jar MyJar.jar

and pray the jar has a manifest with a mainclass .. if not come back ;)

---

### Post by cytg on 2007-10-24
mess around with this

java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel MyApp

java -Dswing.defaultlaf=com.sun.java.swing.plaf.windows.WindowsLookAndFeel MyApp

tell us how it fares ..

---

### Post by fakeollie on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				To make JDarkroom run on Ubuntu 7.10... go to your

<JDarkroom path>/conf/jdarkroom.properties 

and edit it. 

Make sure you have force.full.screen=true

Voila. 

By the way, the problem with JDarkroom is because Gutsy defaults with Xinerama on, and that causes Java to return isFullScreenSupported() as false. This bug is filed and explained in great length here:

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613)

I notified JDarkroom's author, who told me about force.full.screen. It works as a charm. So, this tip is a courtesy of JDarkroom's author, Duncan Jauncey.

---

### Post by shaviro on 2007-10-27
Thanks -- that works.

---

### Post by tonyshangrila on 2007-12-12
Thanks fakeollie, that worked, although I needed one other step--

Since I hadn't run JDarkroom on my Gutsy desktop previously, I had to create the jdarkroom.properties file from scratch.  The fix from the author only worked after running the program from the command line unsuccessfully, then RE-editing the .properties file again.

In any case, thanks for the tip!

---

### Post by a0peter on 2007-12-30
I can't seem to get this to work. When I do java -jar JDarkroom.jar it tells me to upgrade the java. Then I extract the file, adds a conf folder where i create the jdarkroom.properties file and adds the force.full.screen=true. The i create the jar archive again, but this time it says: a0peter@a0peter-laptop: java -jar JDarkRoom.jar
Invalid or corrupt jarfile JDarkRoom.jar

What am I missing?

---

### Post by a0peter on 2007-12-30
Solved.
The original jar created the file and folder (without me having to extract it) in the same directory, from there it was easy editing the jdarkroom.properties.

---

