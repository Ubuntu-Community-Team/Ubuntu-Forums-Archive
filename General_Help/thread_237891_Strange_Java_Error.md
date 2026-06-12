---
title: "Strange Java Error"
date: 2006-08-16
forum: General Help
---

### Post by mikesena on 2006-08-16
Hi,

I am getting a weird java error when trying to run [MoparScape](http://www.moparisthebest.com), a runescape private server.```
root@meo-laptop:/home/meo/Desktop/MoparScape30# ./runMoparScape-linux.sh
Exception in thread "main" java.lang.NoClassDefFoundError: java/lang/StringBuilder
        at Bot.<clinit>(Bot.java:103)
root@meo-laptop:/home/meo/Desktop/MoparScape30# ./runMoparScape-linux.sh
Exception in thread "main" java.lang.NoClassDefFoundError: java/lang/StringBuilder
        at Bot.<clinit>(Bot.java:103)
```

Is there a package I am missing?  Do I need J2SE 1.5, or something like that?  If so, please tell me if I can get it in the package manager.

Ty!

---

### Post by taurus on 2006-08-16
What version of java do you have on your system?

```
java -version
```

---

### Post by mikesena on 2006-08-17
How do I check?  I know I definatly have the default one from [www.java.com](www.java.com), eg. just clicking 'download'.

---

### Post by Zyphrexi on 2007-02-26
java -jar moparscape.jar

or just click the jar file (and open with JRE)

---

