---
title: "Why won't frostwire load?"
date: 2006-10-15
forum: General Help
---

### Post by DiscoSamurai on 2006-10-15
I have java installed (I believe), and previously I Installed frostwire but couldn't get it to work, so I installed Java. That didn't work it starts to open then just closes. What's the problem?

---

### Post by NeoLithium on 2006-10-15
Open up a terminal window and type ```
frostwire
``` Does that give you any errors?

---

### Post by DiscoSamurai on 2006-10-15
zack@zack-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by taurus on 2006-10-15
Please use Automatix to install java on your machine before you attend to run frostwire...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by pete on 2006-10-15
It's also possible you have multiple versions of Java installed, and your machine is defaulting to a version that Frostwire doesn't like.

From a command line, run "sudo update-alternatives --config java"

This command will show you which Java versions you have installed and lets you select among them.  You want the one that looks something like this:

/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

If it's on the list, select it, and Frostwire should work.  If it doesn't show up on the list, try the Automatix route.

---

### Post by Bunyak on 2006-10-16
> **pete said:**
> It's also possible you have multiple versions of Java installed, and your machine is defaulting to a version that Frostwire doesn't like.

From a command line, run "sudo update-alternatives --config java"

This command will show you which Java versions you have installed and lets you select among them.  You want the one that looks something like this:

/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

If it's on the list, select it, and Frostwire should work.  If it doesn't show up on the list, try the Automatix route.

WOOH HOOH! That was the ticket!  Thanks so much!  Frostwire works like a charm now! :mrgreen:

---

### Post by La muerte del DIos on 2006-11-09
Doesn't work for me either.](*,)

---

