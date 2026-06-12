---
title: "Installing/Uninstalling Java for Solaris Studio"
date: 2013-06-14
forum: General Help
---

### Post by nickp008 on 2013-06-14
Hello!

I've recently installed Ubuntu for the first time and I am trying to install Oracle Solaris Studio.  During the installation process i was given this error:

[INDENT]Configuring the installer...
Searching for JVM on the system...
Java installation was not found on this computer
Java 1.5.0_03 or later is required for installing Oracle Solaris Studio. Make sure that Java is properly installed and run installer again.
You can specify valid Java location using --javahome installer argument.

To download Java installation bundle (JDK or JRE), visit [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

[/INDENT]
I then attempted to install java via .rpm and tried installing Solaris again and got the same message.  I then downloaded and attempted to install the java .tar.  But when i unzipped the package i couldn't find a config or install file.  Next I installed OpenJDK from the ubuntu software store. Still the same message.

I then checked to see if java was installed and this was returned:[INDENT]
 java -showversion
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.5) (6b27-1.12.5-0ubuntu0.12.04.1)
OpenJDK Server VM (build 20.0-b12, mixed mode
[/INDENT]

So it appears to me that java is in fact installed. I then located what i assume are the installed java files at /usr/java and attempted to install again using 

[INDENT]$ sudo ./solarisstudio.sh --javahome /usr/java/jdk1.7.0_21/jre
Configuring the installer...
Searching for JVM on the system...
Java Runtime Environment (JRE) was not found at the specified location /usr/java/jdk1.7.0_21/jre
[/INDENT]


I tried every combination of sub and parent folders to the same effect. Could anyone help me?  I tried removing the current java folders to start fresh but it won't let me delete them.

This seems like it should be a very simple thing to do so I'm hoping someone can tell me how i'm being an idiot.


Thanks!!
-Nick

---

### Post by QIII on 2013-06-14
Hello!

So, you are trying to install Java on Ubuntu?

If so, the very easiest method is to use [this](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html).

Best wishes!

---

### Post by nickp008 on 2013-06-14
YES!  I had tried that approach but i must have missed something.  I'm glad i decided to ask instead of fumbling around on my own for the next few hours haha.

Thank you!

---

