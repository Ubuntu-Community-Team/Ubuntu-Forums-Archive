---
title: "How do I install qPSP &amp; PSPVC"
date: 2007-10-07
forum: General Help
---

### Post by kris2pe on 2007-10-07
I've seen this site:
[https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)
But it doesn't seem to work for me!
And I want it placed in the a shortcut!
I hate command lines!

---

### Post by funkyFlash on 2007-11-20
I concur.  I don't hate command lines, as I'm doing this over ssh from work :cool:, but I just hate qmake.  I'm using the latest version, which at the time of this post is 2.0.2.  But qmake comes back with:

```
hdb@filez:~/build/qpspmanager-2.0.2/src$ qmake
Usage: qmake [mode] [options] [files]

   QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

```

Or, if I do it in the top level directory, it makes a makefile, but the makefile doesn't do anything.  It spams my screen with warnings (Makefile:346: warning: overriding commands for target `.cpp.o'
 and so on and so on...), and completes in a fraction of a second.  Also not producing any binaries.

How does I used qmake?

---

### Post by funkyFlash on 2007-11-20
See [this thread]("http://http://thinkingeek.com/qpspmanager/index.php?topic=17.0").  It basically says that qt3 is teh l00z, and you should use qt4.

```
sudo apt-get remove qt3-dev-tools libqt3-mt-dev
sudo apt-get install libqt4-dev
```

Then it's probably a good idea to clean up the qt3 crap with a sudo apt-get autoremove.  Then try the qmake again, and it should be chill.

I'll update the wiki page when I know it works.  It compiled, but I haven't run it yet...

---

### Post by GumbyX on 2007-11-28
> **funkyFlash said:**
> See [this thread]("http://http://thinkingeek.com/qpspmanager/index.php?topic=17.0").  It basically says that qt3 is teh l00z, and you should use qt4.

```
sudo apt-get remove qt3-dev-tools libqt3-mt-dev
sudo apt-get install libqt4-dev
```

Then it's probably a good idea to clean up the qt3 crap with a sudo apt-get autoremove.  Then try the qmake again, and it should be chill.

I'll update the wiki page when I know it works.  It compiled, but I haven't run it yet...

This does work, but the program itself is not made to work with the newest firmware. For some reason the Apps folder only points to GAME150 and ignores all other apps. It also seems to have caused problems on my mem card as now I have lost about 100MB of space on my 4GB mem card. Not sure if its the card or not, but the program has now messed up the cards volume name AND lost me space. Its not looking to be as "good" as everyone keeps saying, or I am just running into too many problems today.

---

