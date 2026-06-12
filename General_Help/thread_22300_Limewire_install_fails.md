---
title: "Limewire install fails"
date: 2005-03-26
forum: General Help
---

### Post by artinla on 2005-03-26
limewire pro 4.4

I get a java error trying to install, but java is installed and working. Is there something else that could cause this?

art@flatulus:~$ sudo sh Lime*.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable. You must install a VM prior to
running this program.

OK So here are my variables:


art@flatulus:~$ java -version
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)
art@flatulus:~$ $echo $PATH
bash: /usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/usr/java/jre1.5.0_02:/usr/java/jre1.5.0_02/bin:
art@flatulus:~$ which java
/usr/java/jre1.5.0_02/bin/java
art@flatulus:~$ $echo $JAVA_HOME
bash: /usr/java/jre1.5.0_02: is a directory
art@flatulus:~$

Thanks,

Art

---

