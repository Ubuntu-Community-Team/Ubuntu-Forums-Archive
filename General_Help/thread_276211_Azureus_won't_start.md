---
title: "Azureus won't start"
date: 2006-10-12
forum: General Help
---

### Post by trommas on 2006-10-12
I have a fresh updated Edgy install.

When I try to start Azureus, it hangs on: "Loading images"

What could this be?

---

### Post by epennings on 2006-10-12
What version of Azureus do you use, the one from the official site, or from the repositories?

What version of Java are you using? You can check by typing 
```
java -version
```
in a terminal.

---

### Post by trommas on 2006-10-13
> **epennings said:**
> What version of Azureus do you use, the one from the official site, or from the repositories?

What version of Java are you using? You can check by typing 
```
java -version
```in a terminal.

I installed Azureus from repositories (through "Add/Remove").

The terminal command gave: 
java version "1.4.2"

---

### Post by epennings on 2006-10-13
You should install a newer Java Runtime to run Azureus

copied from UbuntuGuide.org :

****

How to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox

    * Read #General Notes
    * Read #How to add extra repositories 

```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

    * When asked, agree with DLJ license terms. 

    * To configure J2SE as the default JVM (necessary for programs such as Frostwire, Freenet, RSSOwl and as a plugin for Mozilla Firefox): 

```
sudo update-alternatives --config java
```

Then choose the option that corresponds to J2SE.

****

The Azureus from the repositories is a bit outdated (at least on dapper) and doesnt update well with the auto updater. 

If it doesnt work after updating Java you could try installing from the official site (remove the version from the repositories first): 
[http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?download]("http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux.tar.bz2?download")

Simply extract the archive where you want the program to be. You have to add the launchers (shortcuts) manually.

---

### Post by Peepsalot on 2006-10-15
I have the same problem with azureus, although I'm pretty sure I have the latest java version.
```

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

```
I installed azureus from teh edgy repositories.

---

### Post by Peepsalot on 2006-10-15
Submitted a bug report.
[https://launchpad.net/distros/ubuntu/+source/azureus/+bug/66340](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/66340)

---

### Post by trommas on 2006-10-16
> **Peepsalot said:**
> I have the same problem with azureus, although I'm pretty sure I have the latest java version.
```

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

```I installed azureus from teh edgy repositories.

Thank you for submitting the bug.

I now got Azureus working, installing from the official site (not edgy repo's). Use the guide above to dowload and set it up.. You should be fine..

---

### Post by hotani on 2006-10-26
same here - newest java and azureus from the repos which is version 2.5.0.0

The main window loads then it crashes.

Here is the error:
> 
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=16356, tid=3084547760
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid16356.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
zsh: abort (core dumped)  azureus


Once again I'd like to say, Thanks Edgy! :D

---

### Post by hotani on 2006-10-27
Fixed mine by following [this HOWTO](http://ubuntuforums.org/showthread.php?t=144546) which involves downloading and installing from the azureus site. Make sure to uninstall the current Azureus first - otherwise (like me) you'll end up with 2 identical menu items and no way to tell which is which.

---

### Post by theconley on 2006-10-28
Same.

Are we all using 64-bit?

---

### Post by hotani on 2006-10-28
I'm not, although my hardware is 64 I'm running 32bit Edgy.

---

### Post by ge5239 on 2006-10-28
mine starts, but after that it's kinda ****** up. 


18:04:37  <@ge5239> |GC Warning: Out of Memory!  Returning NIL!
18:04:37  <@ge5239> |GC Warning: Out of Memory!  Returning NIL!
18:04:37  <@ge5239> |Azureus TERMINATED.

that's what i posted in a ircchan before, copied from terminal. 
i get it running for a minute or so, while the "out of memory" is filling up the terminal, and then it crashes. this all worked just fine before i upgraded to 6.10. 

im using the java that was available ~2 months ago, 1.6.0, with the latest beta (automatic update). the new java ran smoothly and required way less resources than i was used to .. :/ 

it's a shame that this happend, loved azureus more than ever.. anyhows, just installed rtorrent, and guess im gonna stick to that unless i get annoyed there instead.. ;-/

---

### Post by duhblow7 on 2006-10-28
Here is what solved it for me.

Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

---

### Post by docomo on 2006-10-29
> **duhblow7 said:**
> Here is what solved it for me.

Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

Thanks, that worked for me as well.

---

### Post by tommcd on 2006-10-29
I installed azureus by the (Alternative Method) listed here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

It does not require java at all, and works fine for me. I am on 32 bit Edgy.

---

### Post by drewnoakes on 2006-11-14
I had problems getting Azureus to work on Ubuntu 6.10 when installed via Synaptic Add/Remove...  It was starting to have problems a few minutes after starting with the error 'Too many files open'.  

In the end, I installed Sun's JVM.  This caused Azureus to disappear after displaying for only a few seconds (perhaps because the version installed via Add/Remove... is compiled for gji).

Ultimately, I downloaded Azureus directly from SourceForge, and now it's running perfectly.

---

### Post by purdticker on 2007-07-26
Fixed this problem for myself...

I had this problem when I installed newest version of java (1.6)

I installed j2re1.4 in synaptic package manager.
> sudo apt-get install j2re1.4

Now when I type "java -version" in terminal it gives me
> $ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

Delete user azureus settings...
> rm -fr ~/.azureus

When I restarted azureus it worked.

---

