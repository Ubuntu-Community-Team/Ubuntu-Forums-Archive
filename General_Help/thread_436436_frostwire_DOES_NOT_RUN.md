---
title: "frostwire DOES NOT RUN"
date: 2007-05-07
forum: General Help
---

### Post by cocotu on 2007-05-07
I installed frostwire from frostwire.com (.deb package) I see it in my menu, I click on it and NOTHING HAPPENS! What is the trick here??

thanks

---

### Post by taurus on 2007-05-07
Do you have java on your system?

Applications -> Accessories -> Terminal
```
java -version
```
Otherwise, try to run it from a terminal to see what the error message is.

```
frostwire
```

---

### Post by cocotu on 2007-05-07
java -version is:
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Error from frostwire is:
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

I was doing  sudo apt-get install sun-java5-bin
Reading package lists... Done
Building dependency tree... Done
Package sun-java5-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-bin has no installation candidate

What is the problem?? thanks

---

### Post by taurus on 2007-05-07
The problem is that you need to install either Sun or Blackdown java first.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by cocotu on 2007-05-08
I installed Sun successfuly and I got this when I ran frostwire:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb107ad03, pid=14280, tid=2967677872
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed03]
#
# An error report file with more information is saved as hs_err_pid14280.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 122: 14280 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I did a java -version and got:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

CONFUSING!

---

### Post by SBFC on 2007-05-08
Which java package did you install? While trying to run Frostwire mine complains that it needs jre1.5+ while saying I have jre1.4.

---

### Post by rainwalker on 2007-05-08
Check out [http://www.ubuntuforums.org/showthread.php?t=305337](http://www.ubuntuforums.org/showthread.php?t=305337)

---

### Post by cocotu on 2007-05-09
As you can see I installed the required java:

I did a java -version and got:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

---

### Post by ironwoodcarver on 2007-05-13
forget frostwire I have had nothing but probs whith that program so I installed limewire pro beta that package is available from their website runs great average 20 cds download a day I love it enjoy

---

### Post by rainwalker on 2007-05-13
I've never had any problems with FrostWire, all my troubles were caused by LimeWire. Installing, setting up, and uninstalling were all a pain.

---

### Post by cocotu on 2007-05-13
Lots of comments NO solutions! thanks...

---

### Post by rsambuca on 2007-05-13
I would consider doing a complete removal of Java using Synaptic, and then re-install it again.  For whatever reason, that worked for me in the past when frostwire stopped working.  It has been working since.

---

### Post by cmost on 2007-05-13
Save yourself the headaches.  Uninstall Java and the Frostwire DEB file you downloaded.  Then, use Automatix2 to install Frostwire.  It will also install the needed Java packages automatically.  If you have more than one version of Java installed, then you simply need to run (in a terminal) sudo update-alternatives --config java.  Choose the latest version of SUN's java and enjoy!  Note:  If you're using Compiz or Beryl, then you'll need a couple additional steps to "see" the Frostwire window.  Let me know if that's the case and I'll tell you how to fix it.

---

### Post by smokinjoe on 2007-05-17
hey cmost.. i think that's my case.. i can't see the frostwire window... it goes blank
i am really thinkin in uninstalling beryl

---

### Post by smokinjoe on 2007-05-17
i unchecked beryl in session but still getting no response from frostwire!!!

need help here..

---

### Post by rainwalker on 2007-05-17
smokinjoe, you can't start FrostWire while Beryl is running, but it should work if you start FrostWire first and than turn on Beryl

---

### Post by cocotu on 2007-05-18
what is Beryl?  I will try your suggestions tonigh. Thanks!

---

### Post by rsambuca on 2007-05-18
You don't need to uncheck Beryl in the sessions menu, just open the beryl-manager and change your window manager to metacity.  Then start frostwire.

If you really wish, there is a small script you can run to have them both running at the same time, but I don't remember it off-hand.  It is in these forums somewhere.

---

### Post by cocotu on 2007-05-21
I will try later after 6PM (New York time) but I'm still not clear about what is Beryl. thanks

---

### Post by cocotu on 2008-01-12
sudo apt-get install sun-java6-bin

thanks!

---

