---
title: "Which Java for LibreOffice Base?"
date: 2015-04-20
forum: General Help
---

### Post by vasa1 on 2015-04-20
I want to learn a little about databases starting from zero. But I found that LibreOffice Base and its newbie-friendly wizards require Java by default. [This page]("http://www.libreoffice.org/get-help/system-requirements/"), in the section for Linux, just says that "For certain features of the software - but not most - Java is required. Java is notably required for Base."

So which Java do I need, the full one direct from Oracle or just *openjdk-7-jre-lib* from the software center? As of now, I don't have any Java-related software installed (Lubuntu 14.04) and haven't much idea about Java or its components.

---

### Post by QDR06VV9 on 2015-04-20
Hi Vasa1 The Link Below might shed some light for you Its below post#3
[http://askubuntu.com/questions/251185/libreoffice-does-not-detect-java-on-fresh-install-of-12-10-how-to-make-it-work](http://askubuntu.com/questions/251185/libreoffice-does-not-detect-java-on-fresh-install-of-12-10-how-to-make-it-work)
Or plainly put
```
 I found a ppa that is maintained and contains scripts that do just that: [launchpad.net/~webupd8team/+archive/java]("https://launchpad.net/%7Ewebupd8team/+archive/java") . For some reason now Libreoffice detects the Oracle JRE.
```
Works good for me:D
Regards

---

### Post by QIII on 2015-04-20
Easy instructions [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

As for OpenJDK versus Oracle Java --

Many don't realize this but OpenJDK is the open source reference implementation for Oracle Java.  That is to say that by decree from Oracle, all things Java must comply with OpenJDK -- including Oracle Java.

That may sound strange until you know that Oracle is the largest contributor to OpenJDK and have a whole department of engineers dedicated to it.

The upshot is that some web developers who are ignorant of that fact seem to turn their noses up at "that open source fake Java" without realizing it dictates what Oracle Java does.  So, some websites don't work with OpenJDK.  Ironic.  If you have the current update of OpenJDK and go to the Oracle Java site to test to see if you have Java, it will say "Congratulations, you have the latest version of Java!"

Equally ironic is the open source devotee who won't use Oracle Java because he'd rather use open source.   It's six of one, a half dozen of the other in this case.  So I just use Oracle Java to make things easy on myself.

Edit:  By the way, Andrew's site there at webupd8.org does not have the Oracle Java binaries.  The installer is a set of scripts that takes care of downloading the binaries and installing them in a way that works with Ubuntu seamlessly.

There is only one distro that gets to actually have Oracle Java installed by default that I know of:  Raspbian.  Maybe Oracle was feeling charitable with raspberrypi.org.

---

### Post by vasa1 on 2015-04-21
Thank you, runrickus and QIII. I'll use the  ppa then.

Marking this [SOLVED]

---

