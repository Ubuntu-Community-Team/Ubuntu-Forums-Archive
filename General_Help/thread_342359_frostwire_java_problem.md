---
title: "frostwire java problem"
date: 2007-01-19
forum: General Help
---

### Post by rabid9797 on 2007-01-19
its not the usual problem either....(i have no idea what im doing here since i know no java at all)

```

$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@eb67e8
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@eb67e8
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@eb67e8
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@eb67e8
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@eb67e8
current thread is Thread[main,5,main]
please submit a bug report to bugs@frostwire.com with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
:~$ 

```

please help

---

### Post by r4ik on 2007-01-20
This might help,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

Good luck !

---

### Post by rabid9797 on 2007-01-28
:| that didn't help at all.

im still stuck too, and anyone help me out here?

---

### Post by PrinceArithon on 2007-01-28
I remember I had the same problem...the thing is I don't remember what the fix was.  All I know is I found the fix in the Frostwire message board.  That is the best I can tell you, which I am really sorry about.

---

### Post by phossal on 2007-01-28
Did you download FrostWire from the FrostWire website?
[edit] Why use FrostWire at all? I know what their website says, buy why not just use LimeWire?

---

### Post by rabid9797 on 2007-01-28
> **phossal said:**
> Did you download FrostWire from the FrostWire website?
[edit] Why use FrostWire at all? I know what their website says, buy why not just use LimeWire?

becuase limewire doesn't even work.

```

~$ limewire
runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")

```

---

### Post by taurus on 2007-01-28
Change the last line in **runLime.sh** to 

```
#!/bin/bash
```

---

### Post by phossal on 2007-01-28
What is the result of this:
```
java -version
```

With Java installed, I'd use LimeWire over FrostWire, and I'd get it and run it like this: [Getting and Running LimeWire]("http://ubuntuforums.org/showthread.php?t=332674#6")

---

### Post by phossal on 2007-01-28
> **taurus said:**
> 

Taurus, what's up with your sig? ;)

---

### Post by taurus on 2007-01-28
> **phossal said:**
> Taurus, what's up with your sig? ;)

You have to ask PriceChild on that.

---

### Post by rabid9797 on 2007-01-28
> **taurus said:**
> Change the last line in **runLime.sh** to 

```
#!/bin/bash
```

yeah yeah i know i fixed it don't worry, im trying to see if limewire works.


> **phossal said:**
> What is the result of this:
```
java -version
```

With Java installed, I'd use LimeWire over FrostWire, and I'd get it and run it like this: [Getting and Running LimeWire]("http://ubuntuforums.org/showthread.php?t=332674#6")

$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
rabid9797@rabid9797-desktop:~$ 

UPDATE: i got limeiwre started and im having the same problem, except this time i don't even get errors from the terminal, the limewire window is just completley blank, just a grey blank window.:mad:

---

### Post by r4ik on 2007-01-28
Forgive me if i ask the obvious but did you  do a

sudo update-alternatives --config java

and choose option 3 ?

---

### Post by rabid9797 on 2007-01-28
> **r4ik said:**
> Forgive me if i ask the obvious but did you  do a

sudo update-alternatives --config java

and choose option 3 ?

i have no option for 3:confused: 

```

$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

---

### Post by phossal on 2007-01-28
You probably want: [LimeWireOther.zip]("http://www.limewire.com/LimeWireSoftOther"). Download it to your desktop and extract it. You can launch it using the LimeWire.jar


cd into the limewire directory
```
java -jar LimeWire.jar
```

[edit] Your java is fine. No need to worry about that.

---

### Post by rabid9797 on 2007-01-28
> **phossal said:**
> cd into the limewire directory
```
java -jar LimeWire.jar
```

[edit] Your java is fine. No need to worry about that.

than why am i still having a problem :confused: 

i got this doing the java command in the directory:

```

rabid9797@rabid9797-desktop:/usr/lib/LimeWire$ java -jar LimeWire.jar
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring

```

---

### Post by phossal on 2007-01-28
Taurus, need your help. Why is his call to Java kicking up errors from the themes? That doesn't make any sense to me?

---

### Post by phossal on 2007-01-28
Did you download LimeWire the way I suggested? Or did you apt-get it or something?

---

### Post by taurus on 2007-01-28
> **phossal said:**
> Taurus, need your help. Why is his call to Java kicking up errors from the themes? That doesn't make any sense to me?

Look at my post #7.  Then, run it again with

```
limewire
```

---

### Post by phossal on 2007-01-28
> **taurus said:**
> Look at my post #7.  Then, run it again with


He should be able to start it directly with java -jar LimeWire though. That doesn't make any sense.

---

### Post by rabid9797 on 2007-01-28
> **phossal said:**
> Did you download LimeWire the way I suggested? Or did you apt-get it or something?

i installed with the rpm from the limewire site and cd'd to the lib folder, than did the java command.

i just downloaded LimeWireOther.zip and did the java command and i got these errors:

```

LimeWire version 4.12.10
Java version 1.5.0_08 from Sun Microsystems Inc.
Linux v. 2.6.17-10-386 on i386
Free/total memory: 889424/2031616

com.limegroup.gnutella.gui.GUILoader$StartupFailedException: invalid themes.jar
	at com.limegroup.gnutella.gui.GUILoader.sanityCheck(GUILoader.java:275)
	at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:48)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.limegroup.gnutella.gui.Main.main(Main.java:44)

STARTUP ERROR!

-- listing properties --
AVERAGE_CONNECTION_TIME=92874
FILTER_HASH_QUERIES=true
DIRECTORIES_TO_SEARCH_FOR_FILES=/media/hdd1/hp/lot14
FRACTIONAL_UPTIME=3.4157315E-4
LAST_EXPIRE_TIME=1169964544290
SESSIONS=3
LAST_ACCEPTABLE_BUG_VERSION=4.13.0
EVIL_HOSTS=BearShare 5.2
DIRECTORY_FOR_SAVING_FILES=/media/hdd1/hp/lot14
UPDATE_DOWNLOAD_DELAY=14400001
RUN_ONCE=true
TOTAL_CONNECTION_TIME=185748
CONTENT_MANAGEMENT_ACTIVE=true
MIN_CONNECT_TIME=7
CLIENT_ID=A5794B876C0801DEE685E1ACF079FF00
CONTENT_AUTHORITIES=fserv1.limewire.com:10000
UPDATE_RETRY_DELAY=1800001
LAST_SHUTDOWN_TIME=1169965275085
EVER_ACCEPTED_INCOMING=true
IDLE_CONNECTIONS=2
PORT=5543
TOTAL_UPTIME=174
AVERAGE_UPTIME=87
UPDATE_GIVEUP_FACTOR=49
UNSET_FIREWALLED_FROM_CONNECTBACK=true
FLUSH_DELAY_TIME=25
TOTAL_CONNECTIONS=2
INSTALLED=true
MAX_SIM_DOWNLOAD=8
UPDATE_DELAY=252000020
WINDOW_Y=112
CONNECTION_SPEED=350
WINDOW_X=860



FILES IN CURRENT DIRECTORY:
/home/rabid9797/Desktop/LimeWire/clink.jar
LAST MODIFIED: 1169848382000
SIZE: 307949

/home/rabid9797/Desktop/LimeWire/commons-httpclient.jar
LAST MODIFIED: 1169848382000
SIZE: 459988

/home/rabid9797/Desktop/LimeWire/commons-logging.jar
LAST MODIFIED: 1169848384000
SIZE: 59154

/home/rabid9797/Desktop/LimeWire/commons-net.jar
LAST MODIFIED: 1169848384000
SIZE: 180799

/home/rabid9797/Desktop/LimeWire/COPYING
LAST MODIFIED: 1169848398000
SIZE: 18349

/home/rabid9797/Desktop/LimeWire/cygwin.bat
LAST MODIFIED: 1169848395000
SIZE: 57

/home/rabid9797/Desktop/LimeWire/cygwin.ico
LAST MODIFIED: 1169848395000
SIZE: 7022

/home/rabid9797/Desktop/LimeWire/daap.jar
LAST MODIFIED: 1169848385000
SIZE: 389560

/home/rabid9797/Desktop/LimeWire/data.ser
LAST MODIFIED: 1169848399000
SIZE: 358

/home/rabid9797/Desktop/LimeWire/donotremove.htm
LAST MODIFIED: 1169848401000
SIZE: 0

/home/rabid9797/Desktop/LimeWire/GenericWindowsUtils.dll
LAST MODIFIED: 1169848392000
SIZE: 12279

/home/rabid9797/Desktop/LimeWire/hashes
LAST MODIFIED: 1169848385000
SIZE: 298

/home/rabid9797/Desktop/LimeWire/i18n.jar
LAST MODIFIED: 1169848385000
SIZE: 25678

/home/rabid9797/Desktop/LimeWire/icu4j.jar
LAST MODIFIED: 1169848386000
SIZE: 741440

/home/rabid9797/Desktop/LimeWire/id3v2.jar
LAST MODIFIED: 1169848386000
SIZE: 94430

/home/rabid9797/Desktop/LimeWire/jcraft.jar
LAST MODIFIED: 1169848386000
SIZE: 137190

/home/rabid9797/Desktop/LimeWire/jdic.jar
LAST MODIFIED: 1169848394000
SIZE: 90644

/home/rabid9797/Desktop/LimeWire/jl011.jar
LAST MODIFIED: 1169848387000
SIZE: 255016

/home/rabid9797/Desktop/LimeWire/jmdns.jar
LAST MODIFIED: 1169848387000
SIZE: 69306

/home/rabid9797/Desktop/LimeWire/libtray.so
LAST MODIFIED: 1169848394000
SIZE: 18501

/home/rabid9797/Desktop/LimeWire/LimeWire.exe
LAST MODIFIED: 1169848401000
SIZE: 122880

/home/rabid9797/Desktop/LimeWire/LimeWire.ico
LAST MODIFIED: 1169848401000
SIZE: 92854

/home/rabid9797/Desktop/LimeWire/LimeWire.jar
LAST MODIFIED: 1169848397000
SIZE: 7177363

```

---

### Post by rabid9797 on 2007-01-28
> **taurus said:**
> Look at my post #7.  Then, run it again with

```
limewire
```

nothing happened, still got the same blank window. (you did mean runLime.sh under /usr/lib/LimeWire right?)

---

### Post by taurus on 2007-01-28
> **rabid9797 said:**
> nothing happened, still got the same blank window. (you did mean runLime.sh under /usr/lib/LimeWire right?)

Yip.

Do you happen to have beryl running?

---

### Post by phossal on 2007-01-28
If you downloaded LimeWire to your desktop... 
Then, in a terminal, you would type this:
```
cd ~/Desktop/Lime*
```
```
java -jar LimeWire.jar
```

The errors you're getting are due to 1 of 2 things: 1, you're not actually in the correct directory, or 2) the themes.jar file is corrupted. I don't believe it's 2. I just downloaded LimeWire myself.

---

### Post by phossal on 2007-01-28
> **taurus said:**
> Do you happen to have beryl running?

That's gonna piss me off. lol I hate beryl.

---

### Post by rabid9797 on 2007-01-28
> **taurus said:**
> Yip.

Do you happen to have beryl running?

yeah. is that a problem? :(

---

### Post by taurus on 2007-01-28
> **phossal said:**
> That's gonna piss me off. lol I hate beryl.

I think beryl will make limewire to behave like that (something to do with video memory thing).

---

### Post by phossal on 2007-01-28
Look... I just downloaded LimeWire over my previous install. I *removed* themes.jar from the LimeWire directory and then tried to restart it (using both my method, and Taurus'): 

Here is what happened:

```
LimeWire version 4.12.6
Java version 1.6.0 from Sun Microsystems Inc.
Linux v. 2.6.17-10-generic on i386
Free/total memory: 3812152/5177344

com.limegroup.gnutella.gui.GUILoader$StartupFailedException: invalid themes.jar
	at com.limegroup.gnutella.gui.GUILoader.sanityCheck(GUILoader.java:275)
	at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:48)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Main.java:44)

STARTUP ERROR!

-- listing properties --
WINDOW_Y=57
FORCE_IP_ADDRESS=true
WINDOW_X=83
PORT=50624
TOTAL_CONNECTION_TIME=1685058
LAST_FWT_STATE=true
UPDATE_DELAY=252000020
UPDATE_GIVEUP_FACTOR=49
FILTER_HASH_QUERIES=true
UPNP_IN_USE=true
INSTALLED=true
FORCED_IP_ADDRESS_STRING=75.46.34.233
AVERAGE_UPTIME=761
TOTAL_UPTIME=3044
MAX_UPLOAD_BYTES_PER_SEC=41
MIN_CONNECT_TIME=7
CONTENT_AUTHORITIES=fserv1.limewire.com:10000
LAST_SHUTDOWN_TIME=1169965374689
APP_WIDTH=952
SESSIONS=4
FORCED_PORT=50624
LAST_ACCEPTABLE_BUG_VERSION=4.13.0
FRACTIONAL_UPTIME=2.0170404E-4
UPDATE_RETRY_DELAY=1800001
CONNECTION_SPEED=350
LAST_EXPIRE_TIME=1169391438108
TOTAL_CONNECTIONS=3
DIRECTORY_FOR_SAVING_FILES=/home/phossal/Desktop/save
MAX_DOWNLOAD_BYTES_PER_SEC=182
UPDATE_DOWNLOAD_DELAY=14400001
RUN_ONCE=true
AVERAGE_CONNECTION_TIME=561686
APP_HEIGHT=766
EVIL_HOSTS=BearShare 5.2
MAX_SIM_DOWNLOAD=8
DIRECTORIES_TO_SEARCH_FOR_FILES=/home/phossal/Desktop/save
UNSET_FIREWALLED_FROM_CONNECTBACK=true
CLIENT_ID=8BEC1D5C9DB67BCB43F70CE636A75E00
FLUSH_DELAY_TIME=25
CONTENT_MANAGEMENT_ACTIVE=true
IDLE_CONNECTIONS=2



FILES IN CURRENT DIRECTORY:
/home/phossal/Desktop/LimeWire/clink.jar
LAST MODIFIED: 1156028319000
SIZE: 307949

/home/phossal/Desktop/LimeWire/commons-httpclient.jar
LAST MODIFIED: 1156028319000
SIZE: 459988

/home/phossal/Desktop/LimeWire/commons-logging.jar
LAST MODIFIED: 1156028319000
SIZE: 59154

/home/phossal/Desktop/LimeWire/commons-net.jar
LAST MODIFIED: 1156028319000
SIZE: 180799

/home/phossal/Desktop/LimeWire/COPYING
LAST MODIFIED: 1156028336000
SIZE: 18349

/home/phossal/Desktop/LimeWire/cygwin.bat
LAST MODIFIED: 1156028330000
SIZE: 57

/home/phossal/Desktop/LimeWire/cygwin.ico
LAST MODIFIED: 1156028330000
SIZE: 7022

/home/phossal/Desktop/LimeWire/daap.jar
LAST MODIFIED: 1156028319000
SIZE: 389560

/home/phossal/Desktop/LimeWire/data.ser
LAST MODIFIED: 1156028336000
SIZE: 358

/home/phossal/Desktop/LimeWire/donotremove.htm
LAST MODIFIED: 1156028337000
SIZE: 0

/home/phossal/Desktop/LimeWire/GenericWindowsUtils.dll
LAST MODIFIED: 1156028325000
SIZE: 12279

/home/phossal/Desktop/LimeWire/hashes
LAST MODIFIED: 1156028319000
SIZE: 298

/home/phossal/Desktop/LimeWire/i18n.jar
LAST MODIFIED: 1156028319000
SIZE: 25678

/home/phossal/Desktop/LimeWire/icu4j.jar
LAST MODIFIED: 1156028319000
SIZE: 741440

/home/phossal/Desktop/LimeWire/id3v2.jar
LAST MODIFIED: 1156028319000
SIZE: 94430

/home/phossal/Desktop/LimeWire/jcraft.jar
LAST MODIFIED: 1156028319000
SIZE: 137190

/home/phossal/Desktop/LimeWire/jdic.jar
LAST MODIFIED: 1156028329000
SIZE: 90644

/home/phossal/Desktop/LimeWire/jl011.jar
LAST MODIFIED: 1156028319000
SIZE: 255016

/home/phossal/Desktop/LimeWire/jmdns.jar
LAST MODIFIED: 1156028319000
SIZE: 69306

/home/phossal/Desktop/LimeWire/libtray.so
LAST MODIFIED: 1156028330000
SIZE: 18501

/home/phossal/Desktop/LimeWire/LimeWire.exe
LAST MODIFIED: 1156028337000
SIZE: 159744

/home/phossal/Desktop/LimeWire/LimeWire.ico
LAST MODIFIED: 1156028337000
SIZE: 92854

/home/phossal/Desktop/LimeWire/LimeWire.jar
LAST MODIFIED: 1156028336000
SIZE: 7120402

/home/phossal/Desktop/LimeWire/LimeWire20.dll
LAST MODIFIED: 1156028326000
SIZE: 40960

/home/phossal/Desktop/LimeWire/LimeWireStub.exe
LAST MODIFIED: 1156028330000
SIZE: 350552

/home/phossal/Desktop/LimeWire/log4j.jar
LAST MODIFIED: 1156028319000
SIZE: 677952

/home/phossal/Desktop/LimeWire/log4j.properties
LAST MODIFIED: 1156028336000
SIZE: 7171

/home/phossal/Desktop/LimeWire/looks.jar
LAST MODIFIED: 1156028319000
SIZE: 630634

/home/phossal/Desktop/LimeWire/MessagesBundle.properties
LAST MODIFIED: 1156028318000
SIZE: 114510

/home/phossal/Desktop/LimeWire/MessagesBundles.jar
LAST MODIFIED: 1156028319000
SIZE: 2951401

/home/phossal/Desktop/LimeWire/mp3sp14.jar
LAST MODIFIED: 1156028320000
SIZE: 40064

/home/phossal/Desktop/LimeWire/pmf.ico
LAST MODIFIED: 1156028337000
SIZE: 3262

/home/phossal/Desktop/LimeWire/ProgressTabs.jar
LAST MODIFIED: 1156028319000
SIZE: 3699

/home/phossal/Desktop/LimeWire/README.txt
LAST MODIFIED: 1156028337000
SIZE: 828

/home/phossal/Desktop/LimeWire/root
LAST MODIFIED: 1156028337000
SIZE: 4096

/home/phossal/Desktop/LimeWire/runLime.sh
LAST MODIFIED: 1169966050000
SIZE: 3012

/home/phossal/Desktop/LimeWire/SOURCE
LAST MODIFIED: 1156028336000
SIZE: 268

/home/phossal/Desktop/LimeWire/spacer.gif
LAST MODIFIED: 1156028337000
SIZE: 49

/home/phossal/Desktop/LimeWire/tritonus.jar
LAST MODIFIED: 1156028320000
SIZE: 152711

/home/phossal/Desktop/LimeWire/update.ver
LAST MODIFIED: 1156028320000
SIZE: 3810

/home/phossal/Desktop/LimeWire/vorbis.jar
LAST MODIFIED: 1156028320000
SIZE: 27215

/home/phossal/Desktop/LimeWire/WindowsFirewall.dll
LAST MODIFIED: 1156028326000
SIZE: 61440

/home/phossal/Desktop/LimeWire/WindowsV5PlusUtils.dll
LAST MODIFIED: 1156028326000
SIZE: 12808

/home/phossal/Desktop/LimeWire/xerces.jar
LAST MODIFIED: 1156028320000
SIZE: 2147687

/home/phossal/Desktop/LimeWire/xml-apis.jar
LAST MODIFIED: 1156028325000
SIZE: 124724

/home/phossal/Desktop/LimeWire/xml.war
LAST MODIFIED: 1156028325000
SIZE: 8423

/home/phossal/Desktop/LimeWire/Incomplete
LAST MODIFIED: 1169966129000
SIZE: 4096


```

You have a corrupt file. Download [LIMEWIRE]("http://www.limewire.com/LimeWireSoftOther"), extract it, and start it.  ](*,)

---

### Post by rabid9797 on 2007-01-28
> **phossal said:**
> Look... I just downloaded LimeWire over my previous install. I *removed* themes.jar from the LimeWire directory and then tried to restart it (using both my method, and Taurus'): 

You have a corrupt file. Download [LIMEWIRE]("http://www.limewire.com/LimeWireSoftOther"), extract it, and start it.  ](*,)

i redownloaded and everything, and im no longer getting the corrupt themes.jar error, but im *still* getting this themes error

```
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading LimeWire:
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring

```
:mad:

EDIT: that's after doing Taurus's fix AND fixing the limewire.sh(replace sh with bash so i can start it correctly)

---

### Post by phossal on 2007-01-28
Open .bashrc
```
sudo gedit ~/.bashrc
```


copy and paste this at the bottom, save and close:
>  export AWT_TOOLKIT=MToolkit 

then:
```
source ~/.bashrc
```


Then start it again. If that works (it should), download Java 6.  :D This problem was resolved in later Java's, and Taurus was right, it's beryl's fault.

---

### Post by rabid9797 on 2007-01-28
> **phossal said:**
> 
Then start it again. If that works (it should), download Java 6.  :D This problem was resolved in later Java's, and Taurus was right, it's beryl's fault.

well, no change in LimeWireOther(same themes error)..but running it from usr/lib got me a much of error messeges. 


```

~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading LimeWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring
Error: Couldn't find per display information

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

```

(i think this is good since the first two are not ones ive seen before?)

anyways, how would i go about downloaded and installing java 6 (and if nesessary removing java 5?)

(a little offtopic, but damn, so far i hadn't run into any problems with beryl, but i knew it was too good last. oh well, hopefully i can get a fix for this *sigh* )

---

### Post by phossal on 2007-01-28
I do it a [little differently,]("http://ubuntuforums.org/showthread.php?t=332674#1") but you can do it this way:
```
sudo apt-get install sun-java6-jdk
```

It's beryl's fault, man. lol

[edit] I'm really bummed out. LimeWire is so pathetically easy to install. Download, Extract, Run. It should've gone a lot easier for you. I hate beryl, but it should still be easier than this.

---

### Post by rabid9797 on 2007-01-28
it still :](*,)  isn't ](*,)  WORKING! ](*,)  :cry:

---

### Post by phossal on 2007-01-28
Have you turned off beryl, mate? That might be a stupid question, because I've never used it. Can't you just *temporarily* get rid of it to test Java?

---

### Post by phossal on 2007-01-28
Check this out: [FrostWire Fix]("http://ubuntuforums.org/showthread.php?t=316398")

So do this:```
sudo gedit ~/.bashrc
```
copy and paste this at the bottom, save and close:```

export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire [COLOR="Red"]#path to frostwire or limewire, edit as necessary[/COLOR]
```

then run:```
source ~/.bashrc
```

Then try to start it.

---

### Post by rabid9797 on 2007-01-28
> **phossal said:**
> Have you turned off beryl, mate?

omg, FINALLY! if you were in front of me right now i would hug you! =D> :mrgreen: 

so i guess from now on i'll have to end beryl to startup limewire. oh well, its not as bad as i thgouht it was going to be.

thank you so much! +100 internets to you good sir!

---

### Post by phossal on 2007-01-28
Rock on. Have a good day/evening. It was fun. lol See my previous post though, because I think that fix will work *with* beryl.

---

### Post by Lux9698 on 2007-07-22
OK guys, I hope someone can lend me some Ideas.
I checked all over the place, in the forums, but nothing works, even If I think the problems are similar.


Installed Java 1.6.0 , Frostwire 4.13.1 Beta and thats the result if I try to start it over Terminal:

~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@4bfe6b
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@4bfe6b
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@4bfe6b
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@4bfe6b
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@4bfe6b
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1206)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:143)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:104)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:72)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:122)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:219)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:327)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)


I think the neccessary port are all open on Firestarter and Router and Beryl is not running.
Firestarter is coming up and it tells me, starting connection, but that it.

PLEASE, someone has any Idea, what going on   ?


Sincerly

---

