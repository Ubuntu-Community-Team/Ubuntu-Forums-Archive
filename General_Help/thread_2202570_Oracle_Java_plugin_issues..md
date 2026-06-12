---
title: "Oracle Java plugin issues."
date: 2014-01-29
forum: General Help
---

### Post by Bigpat on 2014-01-29
Unable to install oracle Java plugin in Google Chrome. I have already created a sym lin with Firefox and it works perfectly. Now whenever I create a sysm link with Google Chrome I still get the please install Java plugin. Does anyone have any iedea. and Please don't say install Iced Tea. I have already remove all of the Ice Tea and only want to use oracle Java. Note that I have a 64bit system.

---

### Post by sergulath on 2014-01-29
Whats your Linux distro? Example: Ubuntu, kubuntu, lubuntu, debian,  xubuntu: 10.04, 11.10, 12.04, 12.10, 13.10 etc..  I need more  information before I can assist.

Also run this in terminal and paste results.

```
java -version
```

---

### Post by Bigpat on 2014-02-01
java version "1.7.0_51"
Java(TM) SE Runtime Environment (build 1.7.0_51-b13)
Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode)
palouidor@Alouidor-desktop:~$

As I said I was able to get firefox symbolic link to the plugin and it works perfectly but not Google Chrome

---

### Post by mayagrafix on 2014-02-01
Why is my version different?

java version "1.7.0_51"
OpenJDK Runtime Environment (IcedTea 2.4.4) (7u51-2.4.4-0ubuntu0.13.10.1)
OpenJDK 64-Bit Server VM (build 24.45-b08, mixed mode)

---

### Post by Bigpat on 2014-02-06
No more worries. I reinstall Ubuntu 32.bit and removed iced tea and all the openjdk and installed oracle java. all is well ad Google Chrome auto picked it up once i created the link with Firefox.

---

