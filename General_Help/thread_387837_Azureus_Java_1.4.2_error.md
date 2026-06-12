---
title: "Azureus Java 1.4.2 error"
date: 2007-03-18
forum: General Help
---

### Post by moot on 2007-03-18
Shortly after starting Azureus I get this error underneath the "Tracker Status" tab:

Error (You are using Java 1.4.2, which is not compatible with your Azureus. Please fix it.)

I installed Java 6 via Dapper-backports (The bin, jre and Firefox plugin), some optional swt packages, cleared my Azureus log files, rebooted Ubuntu and I still get this error.

---

### Post by moot on 2007-03-18
According to java.com's Installation Test I have JRE 1.6.0, the latest version, straight from Sun:

[IMG]http://i48.photobucket.com/albums/f203/goldencream/Random/jre.png[/IMG]

---

### Post by moot on 2007-03-18
No one knows?  This isn't nearly as hard a problem as that uninstallation problem I had earlier.

---

### Post by josephus on 2007-03-19
So I guess you managed to solve your earlier problem, how did you manage that?

I suspect that you have multiple versions of java on your system, one of which is Java 1.4.2 .  Depending on where your files are pointing to, Azureus is using that version.  You might either want to make sure you have uninstalled earlier versions or change the environment variables in Azureus to make sure they are using the right files.  I came across this page which tells you how to do that:

[http://www.azureuswiki.com/index.php/Java](http://www.azureuswiki.com/index.php/Java)

Let me know if this helps.

---

### Post by moot on 2007-03-19
> **josephus said:**
> So I guess you managed to solve your earlier problem, how did you manage that?

I suspect that you have multiple versions of java on your system, one of which is Java 1.4.2 .  Depending on where your files are pointing to, Azureus is using that version.  You might either want to make sure you have uninstalled earlier versions or change the environment variables in Azureus to make sure they are using the right files.  I came across this page which tells you how to do that:

[http://www.azureuswiki.com/index.php/Java](http://www.azureuswiki.com/index.php/Java)

Let me know if this helps.

I'm still not sure, suddenly SPM was able to completely remove Java 5.  Also, according to the terminal command "java -version" I still have Java 1.4.2 on my system.  How do I uninstall this earlier version or change the environmental variables in Azureus?  All that wiki page says is how to install Java on different platforms, and under Dapper Drake it just tells you how to install Java 5.

---

### Post by josephus on 2007-03-19
In the middle of the page in the section "using the new java" it tells how to change the variables

If you only want to affect your Azureus configuration, you can update the azureus shell script by changing : "JAVA_PROGRAM_DIR" to point to your most recent java jre directory.

i'm not sure which libraries you have to remove in synaptic.

---

### Post by josephus on 2007-03-19
Try this, and then select the proper version

```
sudo update-alternatives --config java
```

---

### Post by moot on 2007-03-19
> **josephus said:**
> In the middle of the page in the section "using the new java" it tells how to change the variables

If you only want to affect your Azureus configuration, you can update the azureus shell script by changing : "JAVA_PROGRAM_DIR" to point to your most recent java jre directory.

i'm not sure which libraries you have to remove in synaptic.

Ok, /usr/bin/java points to /usr/lib/jvm/java-gcj/jre/bin/java.  I want it to point to either:

/usr/lib/jvm/java-6-sun/jre/bin/java

or

/usr/lib/Java6/bin/java

Which one is best or appropiate and how exactly do I go about doing that?  The "update-alternatives --config java" doesn't let me use anything other than what I currently have for some reason and the JAVA_PROGRAM_DIR="/usr/lib/*" didn't work at all.


EDIT:  Nevermind, using sudo for "update-alternatives --config java" let me change /usr/bin/java to /usr/lib/Java6/bin/java and now Azureus works just fine.  Thanks a lot, I've been trying to get this to work all day long.

---

### Post by josephus on 2007-03-19
Glad I could help.

---

