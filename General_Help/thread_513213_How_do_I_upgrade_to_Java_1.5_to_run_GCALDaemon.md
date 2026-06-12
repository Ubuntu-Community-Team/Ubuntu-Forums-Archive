---
title: "How do I upgrade to Java 1.5 to run GCALDaemon?"
date: 2007-07-30
forum: General Help
---

### Post by weedenbc on 2007-07-30
I am trying to follow this guide to get GCALDaemon up and running so I can sync Rainbird with my Google Calendar:
[http://gcaldaemon.sourceforge.net/usage.html](http://gcaldaemon.sourceforge.net/usage.html)

I have it all the way to where I actually start the service and I get the following error message:
```

INFO  | GCALDaemon V1.0 beta 13e starting...
FATAL | GCALDaemon requires at least Java 1.5! Current version: 1.4.2
FATAL | Service terminated!
java.lang.Exception: Invalid JVM version!
   at org.gcaldaemon.core.Configurator.<init>(Configurator.java:312)
   at org.gcaldaemon.standalone.Main.main(Main.java:46)

```

So I run system update and there is nothing to update.  I ran the Java Control Panel app and it said
```

JAVA Platform 
Standard Edition 6
Version 1.6.0 (Build 1.6.0-b105)

```

I tried Googling around and even browsing Java's downloads but I didn't see anything that mentioned a version 1.5 for Ubuntu.  Am I missing something here?

---

### Post by dragonwings on 2007-07-30
try applications 
then add/remove 
and search for it should be there

---

### Post by nirpius on 2008-01-02
I have got the same problem and can't find any version later than 1.4 in add/remove.

---

### Post by Lamarque on 2008-01-03
I'm also experiencing the same problem.

---

### Post by jespdj on 2008-01-03
You probably already have Sun Java 6 installed, but it's not being used as the default Java. Enter the following command and select Sun Java 6 as the default Java to be used:
```
sudo update-alternatives --config java
```
If you have not installed Sun Java 6, install it:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by Lamarque on 2008-01-03
> **jespdj said:**
> You probably already have Sun Java 6 installed, but it's not being used as the default Java. Enter the following command and select Sun Java 6 as the default Java to be used:
```
sudo update-alternatives --config java
```
]

That was exactly the problem.  Thank you very much for your help!

---

