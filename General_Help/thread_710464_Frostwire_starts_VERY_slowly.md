---
title: "Frostwire starts VERY slowly"
date: 2008-02-28
forum: General Help
---

### Post by GB2732 on 2008-02-28
On a fresh install of Gutsy, Frostwire starts really slowly. ~3-4min.  I've repaired the connection problem, and otherwise the application works OK. 

I started it in the terminal and get this feedback:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-is
o8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-
*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*
-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-
jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ks
c5601.1987-0" to type FontStruct
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(Cha
tMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:
106)
        at java.lang.Thread.run(Thread.java:619)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@e2fbeb
current thread is Thread[Thread-4,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information
:
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(Cha
tMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:
106)
        at java.lang.Thread.run(Thread.java:619)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@e2fbeb
current thread is Thread[Thread-4,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information
:
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.activate(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.enter(Unknown Source)
        at irc.gui.pixx.PixxTaskBar.addStatus(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(Unknown Source)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(Unknown Source)
        at irc.IRCApplication.sourceCreated(Unknown Source)
        at irc.IRCServer.enumerateSourcesAsCreated(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(Cha                     tMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:                     106)
        at java.lang.Thread.run(Thread.java:619)
SponsorLoader.startElement -> Detected a custom refreshrate -> 0
SponsorLoader.startElement -> Killing Banner Refresh Tasks
BannerContainer.setupBannerRefreshTask() - No banner refresh for me.



Any help is appreciated.

---

### Post by BSAguy on 2008-02-28
I moved over to icedtea instead of java. As I understand it, Icedtea is an open source replacement for java, and it works great. Sun seems to have some serious problems with the last few releases of jre...

After you install icedtea, run:

```
sudo update-alternatives --config java
```

to make sure icedtea is being used.

---

### Post by GB2732 on 2008-02-28
OK, I installed Icedtea and made sure it was being used, but nothing changed. Still takes a long time to load.

---

### Post by GB2732 on 2008-02-29
Any other suggestions?

---

