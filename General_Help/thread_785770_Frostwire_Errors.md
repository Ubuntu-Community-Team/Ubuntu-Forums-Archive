---
title: "Frostwire Errors"
date: 2008-05-07
forum: General Help
---

### Post by OutCell on 2008-05-07
Hi,

I am using Ubuntu Hardy 8.04. I tried installing frostwire couple of times but i keep getting this java errors:
> outcell@outcell-630m:~$ frostwire
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


Can anyone please help me to make it work..
Thanks

---

### Post by vincentvee on 2008-05-10
> **OutCell said:**
> Hi,

I am using Ubuntu Hardy 8.04. I tried installing frostwire couple of times but i keep getting this java errors:


Can anyone please help me to make it work..
Thanks

wish i coukld help you out....am having more trouble too, can't even get an error message, it just don't start

---

### Post by HunterThomson on 2008-05-10
This is the second thread tonight about frost wire and Java errors. In the last thread people were saying that it did work just fine and now they get a java error. I have no help other then it was suggested it was a update that mite have broke it. So, maybe it will be fixed soon....

Or try to reinstall java and see what happens....

---

### Post by OutCell on 2008-05-10
> **HunterThomson said:**
> This is the second thread tonight about frost wire and Java errors. In the last thread people were saying that it did work just fine and now they get a java error. I have no help other then it was suggested it was a update that mite have broke it. So, maybe it will be fixed soon....

Or try to reinstall java and see what happens....

Thanks m8.. I reinstalled java couple of times with no luck.. Is there any limewire alternative for linux? Other than frostwire..

@ vincentvee
It won't start at all, and when i try to start it in terminal i get this error..

---

### Post by ShodanjoDM on 2008-05-10
Have you tried this: [http://ubuntuforums.org/showthread.php?t=778140](http://ubuntuforums.org/showthread.php?t=778140) ?

---

### Post by OutCell on 2008-05-14
> **ShodanjoDM said:**
> Have you tried this: [http://ubuntuforums.org/showthread.php?t=778140](http://ubuntuforums.org/showthread.php?t=778140) ?

Worked like a charm :D thanks!

---

### Post by Exsecrabilus on 2008-05-14
1. Frostwire doesn't work on 64-bit Ubuntu, I hear.

2. Don't you guys know there *is* a Linux release of the latest version of LimeWire?
Just go [here](http://www.limewire.com/download/version.php) to download it. I don't get why people are trying to get FrostWire when they can just get the official version. >_>

---

### Post by krysia on 2008-05-15
install limewire after trying everything suggested nothing worked so I downloaded limewire and all us well.
I would say though that some time ago I installed limewire on w*dows xp and had nothing but trouble with it,but so far so good with ubuntu.

---

### Post by Exsecrabilus on 2008-05-15
Maybe that's because there are less viruses on Ubuntu? :D

---

### Post by strabes on 2008-05-15
> **Exsecrabilus said:**
> I don't get why people are trying to get FrostWire when they can just get the official version.

Because frostwire is open source and free in both senses of the word.

---

