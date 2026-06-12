---
title: "Problem with installing Duplicati"
date: 2015-02-13
forum: General Help
---

### Post by peter1897 on 2015-02-13
I am trying to install Duplicati on Ubuntu server 10.04.4 but i am getting a massage that it needs mono-runtime version 2.6:

```
root@ubuntu:~# dpkg -i "Duplicati 1.3.4.deb"
(Reading database ... 76657 files and directories currently installed.)
Preparing to replace duplicati 1.3.4 (using Duplicati 1.3.4.deb) ...
Unpacking replacement duplicati ...
dpkg: dependency problems prevent configuration of duplicati:
 duplicati depends on mono-runtime (>= 2.6); however:
  Version of mono-runtime on system is 2.4.4~svn151842-1ubuntu4.1.
dpkg: error processing duplicati (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 duplicati

```

How to install the newer mono-runtime version? I tried **apt-get update** but it didn't help.

---

### Post by Holger_Gehrke on 2015-02-13
Ubuntu 10.04 Server is just two month away from EOL. A newer version of mono-runtime is not in the official repositories.
I see three ways to proceed from this point:
[LIST]
[*]Upgrade the server to a newer Ubuntu. 
[*]Try to find a PPA with mono-runtime. 
[*]Get the Duplicati source and compile it yourself to work with the older runtime. 
[/LIST]
All of them sound like a lot of work, with the first alternative being something which will be necessary anyways sooner or later ...

---

### Post by peter1897 on 2015-02-13
Well, i have Ubuntu server installed on virutalbox and for some reason, probably because of the old hardware of my laptop, i can't install newer version of Ubuntu, so the first option will not be available for me. Anyway, i just wanted to test ways to backup mysql database with Duplicati but i will look for some other ways.

---

