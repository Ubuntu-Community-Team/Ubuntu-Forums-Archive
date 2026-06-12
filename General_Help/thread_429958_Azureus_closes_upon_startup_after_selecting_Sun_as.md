---
title: "Azureus closes upon startup after selecting Sun as default Java configuration"
date: 2007-05-01
forum: General Help
---

### Post by Supercross on 2007-05-01
I was having slow speeds when using Azureus and I read on this forum that the default Java config that it uses usually results in slow speeds and to change to Sun Java.  Therefore I used the command:

```
sudo update-alternatives --config java

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
```

to change to selection #2 (this text is obviously after the change) and now Azureus shows the splash screen and as soon as the see the main screen the whole program quits, no messages, nothing, it just exits, and I have to change back to Java selection #3 to allow it to run, although nothing downloads.  My ports are forwarded and I have all green lights in the program but speeds are horribly slow, on par with 56k or worse, alot of the time it is stuck at 0B/s.  Does anyone know what the problem is?

---

### Post by DarthWHO on 2007-05-04
Not sure if you got this working already or not. 

The answer is here: [http://ubuntuforums.org/showthread.php?t=401892](http://ubuntuforums.org/showthread.php?t=401892)

Quick answer:

rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

---

