---
title: "Java applets don't work in web browsers, but Java programs work well"
date: 2008-06-22
forum: General Help
---

### Post by Starlight on 2008-06-22
Hello!

I have a problem with Java in Ubuntu... I have Sun Java 6 installed and it seems to work well outside browsers... Java programs run correctly, Java applets can be run with no problems using appletviewer... but Java doesn't seem to work in any web browser...they say that Java isn't installed. Firefox only has an "Enable Java" checkbox with no additional options, but Opera has a place where you can enter Java path... I seem to have Java installed in /usr/lib/jvm/java-6-sun-1.6.0.06 but I tried entering that path in Opera, it says that it's invalid... and it was the same when I tried entering the path to any of the subdirectories that are inside. How can I make Java work inside web browsers?

---

### Post by gila_monster on 2008-06-22
Check Synaptic and make sure you have sun-java6-plugin installed as well as sun-java6-jre and sun-java6-bin. You need plugin for it to work in the browser.

---

### Post by Starlight on 2008-06-22
Thanks! But there's no such package... the only sun-java6 packages on the list are bin, demo, doc, fonts, javadb, jdk, jre, and source... from these, I have bin, jdk and jre installed.

---

### Post by Zorael on 2008-06-22
Is this on a 32-bit or a 64-bit installation?

At any rate, please post the output of the following commands, entered in a terminal.
```
$ ls -l /usr/lib/mozilla/plugins
$ update-alternatives --display xulrunner-1.9-javaplugin.so
```

---

### Post by Starlight on 2008-06-22
it's 64-bit.

Here's the first output:
> $ ls -l /usr/lib/mozilla/plugins
total 0
lrwxrwxrwx 1 root root 37 2008-04-25 16:50 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

and the second one:
> $ update-alternatives --display xulrunner-1.9-javaplugin.so
No alternatives for xulrunner-1.9-javaplugin.so.

---

### Post by Zorael on 2008-06-22
Okay. Sadly, there is no Sun java browser plugin for 64-bit systems. Don't ask me why, it's beyond me.

The only way for now is to install OpenJDK and the IcedTea plugin.
```
$ sudo aptitude install icedtea-java7-plugin
```
Hopefully that should get it working right away, after a browser restart. If it doesn't, post the output of the same commands as in my last post.

edit: It will likely wrench control from Sun's java and set itself as the default compiler, virtual machine, etc. That can be fixed, though.

---

### Post by Starlight on 2008-06-22
That's really weird... I wonder why it's so hard for them to make a browser plugin when Java is already working well..

ok, thanks! I'm downloading it now :)

edit: it's working now, thanks! :)

edit2: but applets look much worse than when I run them using appletviewer... is it because it set itself as the default compiler? How can I change it?

---

### Post by Zorael on 2008-06-22
Cheers.

Likely OpenJDK has set itself as default for all Java-y stuff now. For general use it's enough, but it's still missing some stuff from Sun's Java that they haven't yet rewritten. They are legally forbidden to release certain parts (licensing), so they're rewriting them from scratch so as to make OpenJDK as good as Sun's.

To check this, enter the following in a terminal.
```
$ java -version
```
If it says the following, then well, OpenJDK is set as the standard.
```
$ java -version
java version "1.6.0"
**OpenJDK** Runtime Environment (build 1.6.0-b09)
**OpenJDK** 64-Bit Server VM (build 1.6.0-b09, mixed mode)
```

***IF*** you really want to use Sun's version instead *(edit: to make your applets look less funky, for instance)*, enter this in a terminal. Pick Sun alternatives where available. Where not, no worries. OpenJDK is generally good enough for most users, so this step is considerably optional.
```
$ for X in `ls -w1 /etc/alternatives/*java* | grep -v .gz`; do sudo update-alternatives --config $X; done
```

Also, please tag thread as solved under Thread Tools.

---

### Post by Starlight on 2008-06-22
Thanks for the answer :) For now I think I prefer to use Sun's Java because it looks better... especially the fonts. Maybe eventually I'll switch back to OpenJDK when they finish it. :) But when I typed that in the terminal, I got an error...here it is:

> $ for X in `ls -w1 *java* | grep -v .gz`; do sudo update-alternatives --config $X; done
ls: cannot access *java*: No such file or directory

ok, I'll tag it after I manage to switch to using Sun's Java :)

---

### Post by Eriol_Ancalagon on 2008-06-22
It's worth mentioning that in the 64-bit forums the sticky simply says to install OpenJDK and the plugin will be enabled, but that did not work for me.  I had to also run the command you indicated above to specifically install the icedtea plugin, which then worked.

---

### Post by Zorael on 2008-06-22
> **Starlight said:**
> But when I typed that in the terminal, I got an error...here it is:
Damn it, my bad, path was relative.
```
$ for X in `ls -w1 **/etc/alternatives/***java* | grep -v .gz`; do sudo update-alternatives --config $X; done
```

---

### Post by Starlight on 2008-06-22
It doesn't find any alternatives for anything... 

> No alternatives for /etc/alternatives/firefox-javaplugin.so.
No alternatives for /etc/alternatives/iceape-javaplugin.so.
No alternatives for /etc/alternatives/iceweasel-javaplugin.so.
No alternatives for /etc/alternatives/java.
No alternatives for /etc/alternatives/javac.
No alternatives for /etc/alternatives/javadoc.
No alternatives for /etc/alternatives/javah.
No alternatives for /etc/alternatives/javap.
No alternatives for /etc/alternatives/javaws.
No alternatives for /etc/alternatives/midbrowser-javaplugin.so.
No alternatives for /etc/alternatives/mozilla-javaplugin.so.
No alternatives for /etc/alternatives/xulrunner-1.9-javaplugin.so.
No alternatives for /etc/alternatives/xulrunner-javaplugin.so.


---

### Post by Zorael on 2008-06-22
Huh. Do you still have Sun's Java installed? That output suggests you don't. :<

```
$ apt-cache policy sun-java6-jre
```

---

### Post by Starlight on 2008-06-25
it seems I have it installed...here's the output:

> $ apt-cache policy sun-java6-jre
sun-java6-jre:
  Installed: 6-06-0ubuntu1
  Candidate: 6-06-0ubuntu1
  Version table:
 *** 6-06-0ubuntu1 0
        500 [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hardy/multiverse Packages
        100 /var/lib/dpkg/status


---

### Post by Zorael on 2008-06-25
I would try reinstalling it, something's not right.
```
$ sudo aptitude reinstall sun-java6-jre
```

---

