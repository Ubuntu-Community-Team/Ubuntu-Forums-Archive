---
title: "Error uninstalling Java 5"
date: 2007-03-18
forum: General Help
---

### Post by moot on 2007-03-18
OK, I tried to run Azureus for the first time since I installed it and after going through the normal configuration process it gave me the following error message under "Tracker Status":

Error (You are using Java 1.4.2, which is not compatible with your Azureus.  Please fix it.)

After browsing through some threads on here on how to install Java I first opted for normal package installs, which installed the Java 5 bin and jre (Packages "sun-java5-bin" and "sun-java5-jre" respectively).  I rebooted and tried Azureus again and got the exact same problem.  Then I found out that Java 6 has been out for a while and installed the package "jdk-6-linux-i586.binjdk-6-linux-i586.bin" straight from Sun using the following 
tutorial:

[http://phossal.com/thread?view=702216931]("http://phossal.com/thread?view=702216931")

After rebooting Azureus is still giving me the same error, and now I can't uninstall Java 5.  Here's the error message I get when I try to uninstall Java 5 via SPM:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory

---

### Post by moot on 2007-03-18
Bump.

---

### Post by josephus on 2007-03-18
Not too sure, but I think that you can force a package to be removed using:

```
dpkg --remove --force-remove-reinstreq <package name>
```

Check the man pages to be sure.

Have you tried uninstalling version 6 first?

---

### Post by moot on 2007-03-18
> **josephus said:**
> Not too sure, but I think that you can force a package to be removed using:

```
dpkg --remove --force-remove-reinstreq <package name>
```

Check the man pages to be sure.

Have you tried uninstalling version 6 first?

I just tried to uninstall version 6 and I got the same error.  I tried to use that force remove command but I need to tell it to remove the bin and jre simultaneously.

---

### Post by moot on 2007-03-18
Bump.

---

### Post by moot on 2007-03-18
I just asked this question on the Ubuntu help IRC channel and I was told that I was basically screwed.

---

### Post by DigitalVortex on 2007-03-21
I had this issue after installing the java 6 (no prev version was installed) because I attempted to remove it.  I too am new and basically playing a lot to learn.  Anyway, as you said you did your stuff via SPM, select each individual package (I would start with the java 6 ones) and go to Edit, Fix broken packages.

Note, I had to have something selected for it to work.  And when it did work, I vaguely recall a message in the lower left status bar of SPM saying that broken dependencies were fixed.  Result --- I was able to remove the java 6 package.

Good Luck!

---

