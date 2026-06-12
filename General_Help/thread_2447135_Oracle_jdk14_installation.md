---
title: "Oracle jdk14 installation"
date: 2020-07-13
forum: General Help
---

### Post by arjun13 on 2020-07-13
Hey Guys, I am using Ubuntu 20.04 amd64 and am trying to install Oracle JDK 14 and have downloaded the file: jdk-14.0.1_linux-x64_bin.deb which I am attempting to install using the command:

$ sudo dpkg -i Downloads/jdk-14.0.1_linux-x64_bin.deb

However, after installation, when I try to see whether java is installed using:

$ javac -version

OR

$ java -version

It doesn't show any output. What's going wrong?

Thanks!


SOLVED

---

### Post by slickymaster on 2020-07-13
Thread moved to **General Help** for a better fit

---

### Post by ActionParsnip on 2020-07-13
[https://tecadmin.net/install-java-ubuntu-20-04/](https://tecadmin.net/install-java-ubuntu-20-04/)

Try that

---

### Post by arjun13 on 2020-07-13
I read the URL you provide and after the command:
$ sudo dpkg -i jdk-14.0.1_linux-x64_bin.deb

I use the following command:
$ update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-14.0.1/bin/java 100

To check whether Java is installed:
$ java -version
java version "14.0.1" 2020-04-14
Java(TM) SE Runtime Environment (build 14.0.1+7)
Java HotSpot(TM) 64-Bit Server VM (build 14.0.1+7, mixed mode, sharing)


However:
$ javac -version

Command 'javac' not found, but can be installed with:.....

Also, the command:
$ whereis java
java: /usr/bin/java /usr/share/java

I think that it installed JRE and not JDK.
How can I fix this?

Thanks!

---

### Post by Holger_Gehrke on 2020-07-13
update-alternatives updates the link-structure for a single program file (in this case /usr/bin/java is linked to /etc/alternatives/java which then points to the actual executable). You can either use update-alternatives for every single executable that's part of the jdk or use update-java-alternatives which will do it in one stroke for a whole jdk / jre.

Holger

---

### Post by arjun13 on 2020-07-13
Can you provide the command using "update-java-alternatives"?

---

### Post by Holger_Gehrke on 2020-07-13
Use 'update-java-alternatives --list' to get the names of the java runtime environments and java development kits for which there are '."name".jinfo' files in /usr/lib/jvm, then use 'update-java-alternatives --set "name"' to set an alternative to use. The "name" is shown in the first column of the output of  'update-java-alternatives --list'.

Holger

PS: like for most commands, there's a man page for update-java-alternatives.

---

