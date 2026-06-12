---
title: "Frostwire Locks Up"
date: 2008-02-26
forum: General Help
---

### Post by thewho443 on 2008-02-26
When I run frostwire it works until I click an action button and then freezes up.  This is what I get when I run it in the terminal:

[INDENT]Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.7.0]
Configuring environment...
Loading FrostWire:
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(URLClassLoader.java:221)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:209)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:324)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:269)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:337)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:187)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:106)
        at java.lang.Thread.run(Thread.java:675)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@66eb46
current thread is Thread[Thread-7,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1311)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:106)
        at java.lang.Thread.run(Thread.java:675)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@66eb46
current thread is Thread[Thread-7,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1311)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:106)
        at java.lang.Thread.run(Thread.java:675)
SponsorLoader.startElement -> Detected a custom refreshrate -> 0
SponsorLoader.startElement -> Killing Banner Refresh Tasks
BannerContainer.setupBannerRefreshTask() - No banner refresh for me.


[/INDENT]

Any help on this issue would be useful.

Thanks

---

### Post by taurus on 2008-02-26
You are running java version 1.7!  What's the output of this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by thewho443 on 2008-02-26
I ran the command and tried the java 1.6 and 1.5 and I got this both times instead:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct

---

### Post by alwayshere on 2008-02-27
i have frostwire running on 7,04 fiesty with

sun java6 jre

and 
sun java6-plugin

go to synaptic package manager. and see if they are both there

when i first trird to start frost wire it all started up fine but it would not connect to net because of firewall  so i had to copy and past a file into frost wire  main files to fix it  sorry i looked but cant find it for ya but it is on forumssome where . the other option that may work for t hat is to install firstarter firwall and that may help to give access to net  for frostwire  eg try start frost  wire and firestarter pop up ask ya to allow net acess to frost wire .

---

