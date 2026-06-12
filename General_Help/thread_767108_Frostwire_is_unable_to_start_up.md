---
title: "Frostwire is unable to start up"
date: 2008-04-25
forum: General Help
---

### Post by petaloid on 2008-04-25
Hello all,
I recently acquired frostwire and have tried to get it working. I installed it from teh site using the deb package. I also have the up to date version of Java. However when I run frostwire in the terminal I get the folowing error:
__________________________________________________________________________
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
___________________________________________________________________________

That is the end of the error. I have a standard Hardy Heron 8.04 computer with the normal architecture.

Thanks for any help that is provided.

---

### Post by bigbrovar on 2008-04-25
sudo update-java-alternatives -s java-6-sun  

that should do it :)

---

### Post by petaloid on 2008-04-26
Thank you! It works now :D

---

### Post by SomeGayDude on 2008-04-28
I'm having the same problem with Frostwire.  I tried the command and I get this:

master@master-desktop:~$ sudo update-java-alternatives -s java-6-sun
[sudo] password for master: 
sudo: update-java-alternatives: command not found
master@master-desktop:~$ 

Oh, when I saw the background for 8.04 all I could this of is "Piece out Dude!" and "Flower Power Child"

Any ideas?

---

