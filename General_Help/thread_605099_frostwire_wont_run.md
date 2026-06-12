---
title: "frostwire wont run"
date: 2007-11-06
forum: General Help
---

### Post by scarecrow123 on 2007-11-06
frostwire wont do anything when i click on the icon or go to apps\internet\frostwire
any help would be appreciated

---

### Post by Maestro23 on 2007-11-06
Do you have java installed?

---

### Post by scarecrow123 on 2007-11-06
i think so,this pops up when i try and change the version

mark@Scarecrow:~$ sudo update-alternatives --config java
Password:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java

---

### Post by rsambuca on 2007-11-06
Just type 'frostwire' in a terminal to run it.  It will give you an error message.  My guess, though, is that you don't have the proper version of java installed.

---

### Post by taurus on 2007-11-06
That's the wrong version.  You need the Sun's java.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by scarecrow123 on 2007-11-06
i ran the code 
Code:

sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version

and it went through and installed it i think but frostwire still wont run

---

### Post by taurus on 2007-11-06
What are the outputs of these two commands from a terminal?

```
java -version 
frostwire
```

---

### Post by rsambuca on 2007-11-06
Are you running the 64bit version of Ubuntu by chance?  If so, you will have to run 

sudo apt-get install ia32-sun-java6-bin

and then switch to that version of java prior to running frostwire.

---

### Post by scarecrow123 on 2007-11-06
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

 this is the outcome of the two commands

sudo apt-get install ia32-sun-java6-bin
i tried this command too and this is what it said
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ia32-sun-java6-bin

---

### Post by taurus on 2007-11-06
Try to reconfigure your java again and make sure you pick Sun's java version as your default one.

```
sudo update-alternatives --config java
```

---

### Post by scarecrow123 on 2007-11-06
it still just gives me these tow options

Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java

---

### Post by rsambuca on 2007-11-06
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by scarecrow123 on 2007-11-06
its still saying 
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java

---

### Post by taurus on 2007-11-06
Post the complete output of this command here.

```
sudo apt-get install sun-java6-bin
```

---

### Post by scarecrow123 on 2007-11-06
mark@Scarecrow:~$ sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-bin

---

### Post by rsambuca on 2007-11-06
Go to your top menu bar and select "System -> Administration -> Software Sources".  Make sure the Universe and Multiverse repositories are checked.  Then close the Software Sources and click OK to reload your repositories.  Then try installing the java again.

---

### Post by scarecrow123 on 2007-11-06
i saw that on a thread earlier, i dont have an option of software sources. any idea where else i can get to it?

---

### Post by rsambuca on 2007-11-06
If you open the Synaptic Package Manager, then go to the top "Settings", and then "Repositories" will get you to the same place.

It is strange that it is not in your menu in the first place.  What version of Ubuntu are you using?

---

### Post by scarecrow123 on 2007-11-06
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

---

### Post by scarecrow123 on 2007-11-06
i turned on the multiverse and the universe options now im pretty sure

---

### Post by scarecrow123 on 2007-11-06
it finally opens and runs, thanks for all your help
i really appreciate it

---

### Post by Maestro23 on 2007-11-06
> **scarecrow123 said:**
> it finally opens and runs, thanks for all your help
i really appreciate it

Good deal. Don't forget to mark this SOLVED using the Thread Tools.

Thanks.:)

---

### Post by ghettosamson on 2007-12-25
@rsambuca.
My froswire wouldn't open either. Im running the 64 bit version. The command
sudo apt-get install ia32-sun-java6-bin
solved my problem. Now it runs, but it wont connect. Now what. Thanks and happy holidays.

---

### Post by rsambuca on 2007-12-25
> **ghettosamson said:**
> @rsambuca.
My froswire wouldn't open either. Im running the 64 bit version. The command
sudo apt-get install ia32-sun-java6-bin
solved my problem. Now it runs, but it wont connect. Now what. Thanks and happy holidays.

Run frostwire from a terminal and see what error message(s) get spit out.  Just type

```
frostwire
```

---

### Post by ghettosamson on 2007-12-25
here is what outputs

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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:106)
        at java.lang.Thread.run(Thread.java:619)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@15b0333
current thread is Thread[Thread-6,5,main]
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:106)
        at java.lang.Thread.run(Thread.java:619)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@15b0333
current thread is Thread[Thread-6,5,main]
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
        at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:147)
        at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:106)
        at java.lang.Thread.run(Thread.java:619)
SponsorLoader.startElement -> Detected a custom refreshrate -> 0
SponsorLoader.startElement -> Killing Banner Refresh Tasks
BannerContainer.setupBannerRefreshTask() - No banner refresh for me.


thank you in advance.

---

