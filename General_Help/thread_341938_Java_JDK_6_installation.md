---
title: "Java JDK 6 installation"
date: 2007-01-19
forum: General Help
---

### Post by ghepardo on 2007-01-19
I tryed to install jdk 6 from the rpm package (using alien to convert it to a deb package) download from java.sun.com, but I get errors:

```

anu@manu-desktop:~/Downloads/Java$ sudo alien -d jdk-6-linux-i586.rpm --scripts
jdk_1.6.0-1_i386.deb generated
manu@manu-desktop:~/Downloads/Java$ sudo dpkg -i jdk_1.6.0-1_i386.deb
Selecting previously deselected package jdk.
(Reading database ... 133581 files and directories currently installed.)
Unpacking jdk (from jdk_1.6.0-1_i386.deb) ...
Setting up jdk (1.6.0-1) ...
-en Unpacking JAR files...

-en     rt.jar...

-en     jsse.jar...

-en     charsets.jar...

-en     tools.jar...

-en     localedata.jar...

-en     plugin.jar...

-en     javaws.jar...

-en     deploy.jar...

[: 912: ==: unexpected operator
[: 912: ==: unexpected operator

```

---

### Post by ghepardo on 2007-01-22
up

---

