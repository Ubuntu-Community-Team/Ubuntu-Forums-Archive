---
title: "frostwire wont work"
date: 2008-06-27
forum: General Help
---

### Post by Russty of Oz on 2008-06-27
Hi

I have just installed frostwire on 8.04 and when I try to run it nothing happens.  I did it in the terminal and got this output, but what does it all mean?

russty@russty-desktop:~$ frostwire
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



Russty.

---

### Post by latna on 2008-06-27
> java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so

Does this file exist on your system? Maybe you need to install some other package to get it. Although apt should have taken care of that I would think.

For the record, I have sun-java5 installed not openjdk, and frostwire works with it. For me this file belongs to the sun-java5-bin package. I can't find an equivalently named package for openjdk though.

---

### Post by Russty of Oz on 2008-06-29
Ah, I see.  I will see if I can put in the Java package.

Thanks.

---

### Post by Russty of Oz on 2008-06-29
I uninstalled the openjdk in synaptic and now it works!

Russty.

---

