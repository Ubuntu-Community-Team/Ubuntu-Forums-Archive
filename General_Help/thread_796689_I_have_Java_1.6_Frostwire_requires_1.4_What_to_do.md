---
title: "I have Java 1.6 Frostwire requires 1.4 What to do?"
date: 2008-05-16
forum: General Help
---

### Post by Roasted on 2008-05-16
What the title says... Running Hardy, java issue, it won't run on 1.6. It requires 1.4.

---

### Post by amaroKer on 2008-05-16
I would switch to GTK-Gnutella.  Much easier on the hardware, and seems to DL much faster for me.

---

### Post by strabes on 2008-05-16
Very strange, I have the sun-java6-jre package installed and limewire runs just fine on my computer.

---

### Post by Roasted on 2008-05-16
This is frostwire. I'm not sure how different they are.

Frostwire just wouldn't boot. But when I boot it from terminal, I get this.



jason@jason-hardy:~$ frostwire
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

jason@jason-hardy:~$

---

### Post by ludovicc on 2008-05-17
Hello,

I tried also to install Frostwire on Ubuntu 8.04 / 64 bits / sun-java-6, but it doesn't work for me also. Looking at the logs, there is an issue with one of the linked libraries provided by Frostwire, so my guess is that they have not included a library for 64bits. The best solution at this point is to file a bug report with the Frostwire team. 

The issue is not caused by Java, most programs which work on Java 1.4 will work fine on Java 6.

Ludovic

---

### Post by ludovicc on 2008-05-17
Looking at the Frostwire forum, here is a solution that might work for 64bit machines:
[http://www.frostwire.com/forum/viewtopic.php?f=1&t=4219&sid=6d91da034dbb31f338bf794cee46a790#p15729](http://www.frostwire.com/forum/viewtopic.php?f=1&t=4219&sid=6d91da034dbb31f338bf794cee46a790#p15729)

---

### Post by benevolent on 2008-05-18
Hm... what about the 32-bit??? Same problem here

---

### Post by Mze on 2008-05-18
See if you can find a solution [here]("http://ubuntuforums.org/showthread.php?t=615734&page=2")

---

### Post by benevolent on 2008-05-22
Thank you very much! Now it's working ;-)

---

### Post by Mr_bleu on 2008-05-22
I get a problem too when loading frostwire:

[I]djr@popeye-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-wenquanyi-wenquanyi zenhei-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@6e3e5e
current thread is Thread[Thread-6,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(EventDispatcher.java:293)
        at irc.ListenerGroup.sendEventEx(ListenerGroup.java:169)
        at irc.ListenerGroup.sendEvent(ListenerGroup.java:143)
        at irc.ListenerGroup.sendEvent(ListenerGroup.java:211)
        at irc.gui.pixx.PixxTaskBar.enter(PixxTaskBar.java:152)
        at irc.gui.pixx.PixxTaskBar.addStatus(PixxTaskBar.java:207)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(PixxMDIInterface.java:250)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(PixxMDIInterface.java:330)
        at irc.IRCApplication.sourceCreated(IRCApplication.java:325)
        at irc.IRCServer.enumerateSourcesAsCreated(IRCServer.java:301)
        at irc.IRCApplication.newServer(IRCApplication.java:166)
        at irc.IRCApplication.init(IRCApplication.java:133)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:149)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:107)
        at java.lang.Thread.run(Thread.java:619)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@6e3e5e
current thread is Thread[Thread-6,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(EventDispatcher.java:293)
        at irc.ListenerGroup.sendEventEx(ListenerGroup.java:169)
        at irc.ListenerGroup.sendEvent(ListenerGroup.java:143)
        at irc.ListenerGroup.sendEvent(ListenerGroup.java:211)
        at irc.gui.pixx.PixxTaskBar.activate(PixxTaskBar.java:398)
        at irc.gui.pixx.PixxTaskBar.enter(PixxTaskBar.java:153)
        at irc.gui.pixx.PixxTaskBar.addStatus(PixxTaskBar.java:207)
        at irc.gui.pixx.PixxMDIInterface.statusCreated(PixxMDIInterface.java:250)
        at irc.gui.pixx.PixxMDIInterface.sourceCreated(PixxMDIInterface.java:330)
        at irc.IRCApplication.sourceCreated(IRCApplication.java:325)
        at irc.IRCServer.enumerateSourcesAsCreated(IRCServer.java:301)
        at irc.IRCApplication.newServer(IRCApplication.java:166)
        at irc.IRCApplication.init(IRCApplication.java:133)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:149)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:107)
        at java.lang.Thread.run(Thread.java:619)
Smileys should be ACTIVE!
SponsorLoader._loadBanners() exception java.net.UnknownHostException: sponsors.frostwire.com
UpdateMessageReader.readUpdateFile() exception java.net.UnknownHostException: update.frostwire.com
                                                                           [/I]

I'm running kUbuntu.

---

### Post by ludovicc on 2008-05-25
Like the logs said, report the problem to [email]bugs@frostwire.com[/email]. There is nothing in that error message that seems to indicate that it's related to Ubuntu or your installed Java VM.

Actually, those lines seem to indicate some internal program assertion that failed: 
expected thread was [Lirc.DispatchThread;@6e3e5e
current thread is Thread[Thread-6,5,main]

Ludovic

---

### Post by Roasted on 2008-05-25
> **ludovicc said:**
> Like the logs said, report the problem to [email]bugs@frostwire.com[/email]. There is nothing in that error message that seems to indicate that it's related to Ubuntu or your installed Java VM.


Except for the fact it specifically tells me that it's a problem with my Java...

Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"

---

### Post by ludovicc on 2008-05-26
I was replying to Mr_Bean... 

For your problem, have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=615734&page=2"), other people seem to be able to run Frostwire now.

---

### Post by Roasted on 2008-06-18
All right. It's been 3 weeks. I let the problem settle and came back to it. I did a complete removal of frostwire and re-downloaded the deb package and installed it.

Same problem.

Anything?

edit - somehow I missed the previous post...

---

