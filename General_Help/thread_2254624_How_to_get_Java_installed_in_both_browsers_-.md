---
title: "How to get Java installed in both browsers - ?"
date: 2014-11-28
forum: General Help
---

### Post by michael-piziak on 2014-11-28
I just installed ubuntu on my sisters computer (version 12.04 64bit).

I have Firefox and Chromium web browsers, yet neither has Java enabled.

Please advise on how to install Java for both browsers.

---

### Post by nerdtron on 2014-11-28
You can search java from the software and try to install that.

From the command line:
```
 sudo apt-get update && sudo apt-get install default-jre icedtea-plugin
```

Works on firefox only as I tested.

---

### Post by QIII on 2014-11-28
Google dropped support for NPAPI in Chrome -- and Java went with it.  The upshot is that Java will not work with Chrome from here on out unless someone finds a way to do it by means of a hack.

If you want Oracle Java instead of OpenJDK, you can also follow the link in my signature and look for "Using webupd8's strikingly simple method" to use webupd8's scripts.  You can install either Oracle Java 7 or Oracle Java 8.

Bear in mind that OpenJDK is the open source reference implementation for Oracle Java.  That is, Oracle itself has declared that all things Java must comply with OpenJDK to be called "Java" -- even Oracle Java.  (Oracle is one of the largest movers and shakers in OpenJDK development, so don't let yourself believe that OpenJDK is really, truly divorced from Oracle.)  But there are many web developers who didn't seem to get the memo and so their sites may balk at OpenJDK.

---

### Post by michael-piziak on 2014-11-28
hmmmm,

Should I add Java to the systems 2 browsers (Firefox and Chromium), or is Java slowly dying ?

If it is recommended to add it, what's the best way to do it - terminal code line(s) or software center (I seen something called icetea in there).

---

### Post by nerdtron on 2014-11-28
> hmmmm,

Should I add Java to the systems 2 browsers (Firefox and Chromium), or is Java slowly dying ?

I don't know. Depends on whether you really need it or not.

> If it is recommended to add it, what's the best way to do it - terminal code line(s) or software center (I seen something called icetea in there).

They should be the same. I haven't open the software center since it's kinda slow to load but I think you should try it first.
Remember to restart you browser after the installation, then go to [http://javatester.org/](http://javatester.org/) to test of java is installed. (on firefox there's a notification if you want to grant java access on the page).

---

### Post by michael-piziak on 2014-11-28
I installed IcedTea.
The URL you suggested (javatester.org) won't recognize java is installed in Firefox or Chromium
HOWEVER, if I go to this page, both browsers say a java version is installed:   [http://service.parachat.com/knowledgebase/194/How-can-I-test-whether-Java-is-working-on-my-computer.html](http://service.parachat.com/knowledgebase/194/How-can-I-test-whether-Java-is-working-on-my-computer.html)

The java is working at [www.doperoms.com](www.doperoms.com), with both browsers, where it didn't work before, so I think the problem is solved.

Thread marked as solved.

---

