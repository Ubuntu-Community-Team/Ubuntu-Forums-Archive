---
title: "Making the default Java version different between programs"
date: 2007-05-23
forum: General Help
---

### Post by Natume on 2007-05-23
Not sure if this is the most appropriate place for this question, but oh well.  Basically... is it possible to have different programs use a different version of Java, say (or any requisite components, really), by default?

Right now I'm running both Freemind 0.9.0 and Azureus (whatever the lastest version is) on my computer, and unfortunately, they each don't like specific versions of Java.  Azureus doesn't like to work with the Sun Java 5.0, whereas Freemind only works with Sun Java versions.  I know how to change the default version with 'sudo update-alternatives --config java' just fine, but is there a way to make different programs use different versions simultaneously (perhaps with update-alternatives)?  It would be great if I could use both Freemind and Azureus without having to flop the version every few hours {chuckles}.

Thanks for taking the time to read this.

~Natume

---

### Post by Jorge on 2007-06-22
This is from the [_Freemind Wiki page_]("http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux"):

How can I make FreeMind use a specific Java Virtual Machine?

If you've installed FreeMind from a package, you can make it use a different Java virtual machines than other programs by adding lines similar to the 2 following ones to /etc/freemind/freemindrc, for all users, or to $HOME/.freemind/freemindrc, for you, so that only FreeMind is impacted (and no other program):

```
   export PATH=$PATH:*/usr/java/j2re1.4.2_04/bin*
   export JAVA_HOME=*/usr/java/j2re1.4.2_04*
```

(the part in italic depends on your installation)

Hope it works... Post results here, please.

---

### Post by stchman on 2007-06-22
> **Natume said:**
> Not sure if this is the most appropriate place for this question, but oh well.  Basically... is it possible to have different programs use a different version of Java, say (or any requisite components, really), by default?

Right now I'm running both Freemind 0.9.0 and Azureus (whatever the lastest version is) on my computer, and unfortunately, they each don't like specific versions of Java.  Azureus doesn't like to work with the Sun Java 5.0, whereas Freemind only works with Sun Java versions.  I know how to change the default version with 'sudo update-alternatives --config java' just fine, but is there a way to make different programs use different versions simultaneously (perhaps with update-alternatives)?  It would be great if I could use both Freemind and Azureus without having to flop the version every few hours {chuckles}.

Thanks for taking the time to read this.

~Natume

Make scripts and call the different versions of Java.  You can do something like this.

Script 1
/usr/bin/j2_1.4.0.1 -classpath /home/joe/ App1 &

Script 2
/usr/local/bin/j2_1.5.0_2 -classpath /home/joe App2 &

Each script will execute a different JRE.  Of course you will have to install and include the paths to each version.

---

