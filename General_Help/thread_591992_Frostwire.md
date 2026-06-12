---
title: "Frostwire"
date: 2007-10-26
forum: General Help
---

### Post by Kyrian on 2007-10-26
I've been having trouble running Frostwire in Gutsy, just installed it two days ago.

I've installed Java runtime enviorment, and any of the latest Java updates available, restarted my computer, etc, yet it is still a blank icon.

Any ideas? :confused:
> 
kyrian@kyrian-desktop:~$ frostwire&
[1] 6163
kyrian@kyrian-desktop:~$ Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)


That's the message I get when I try to run the Frostwire command via terminal.

It plainly says I have an outdated version, when, I've updated everything.

---

### Post by kast on 2007-10-26
try 
[B]
update-java-alternatives --list[/B]

see how many version might be installed, then

**sudo update-java-alternatives --set** <one of the java versions>

---

### Post by divague on 2007-10-26
try running this command in a terminal

sudo update-alternatives --config java

and select the path to the new version

---

### Post by Kyrian on 2007-10-26
Bah, > java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-6-sun 63 /usr/lib/jvm/java-6-sun

Yet I've downloaded and upgraded from their site.

=/

***EDIT-- ***

Diva's worked. Thanks!

---

