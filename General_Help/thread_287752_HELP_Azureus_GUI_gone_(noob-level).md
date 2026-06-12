---
title: "HELP: Azureus GUI gone (noob-level)"
date: 2006-10-29
forum: General Help
---

### Post by Zyyke on 2006-10-29
Have Ubuntu 6.01 Dapper installed with newest repository Azureus. Everything have been working fine, untill last reboot. When starting Azureus, I do not get the GUI :confused: 

When checking, it appeares that Azureus IS running, just not showing the user interface. Anyone have any suggestion for how to solve this problem? Im a "noob", so easy descriptions would be appreciated ...

---

### Post by makeyre on 2006-10-29
> **Zyyke said:**
> Have Ubuntu 6.01 Dapper installed with newest repository Azureus. Everything have been working fine, untill last reboot. When starting Azureus, I do not get the GUI :confused: 

When checking, it appeares that Azureus IS running, just not showing the user interface. Anyone have any suggestion for how to solve this problem? Im a "noob", so easy descriptions would be appreciated ...

I'm not a noob, and I'm having this problem as well in Edgy (6.10).  Previous bugs were filed on similar issues such as the interface being not clickable.  

I start Azureus up, close the "What's new in 2.5.0.0" window, and then there is no system tray icon for azureus.  ps -ef |grep azureus shows that it is running through java.  My java, by the way, is the Sun 5.0 version.

```
>sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

---

### Post by Zyyke on 2006-10-29
Solved the problem by downloading the Azureus 2.5.0.0 build, and installing it manually following  [this guide]("http://azureus.sourceforge.net/howto_linux.php"). Apparently the repository version is not up to date. This also solved the problem with not being able to close or hide system tray pop-up notices.

---

### Post by makeyre on 2006-11-25
So this is definitely a persistent problem which has not been addressed yet?  The fix seems to be to not use the packaging system at all for Azureus, or download and overwrite the packaged version.  What would it take for someone to issue an upgrade for this package since it's not fully working?  Or can that only happen in Ubuntu 7.04?  I hate breaking the package system by replacing programs manually or using Automatix because I'm not sure what will break on the next upgrade.

People have reported the same bug in other threads:
[http://ubuntuforums.org/showthread.php?t=293277](http://ubuntuforums.org/showthread.php?t=293277)
[http://ubuntuforums.org/showthread.php?t=297999](http://ubuntuforums.org/showthread.php?t=297999)

---

