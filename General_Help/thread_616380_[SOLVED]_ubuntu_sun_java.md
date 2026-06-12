---
title: "[SOLVED] ubuntu sun java"
date: 2007-11-18
forum: General Help
---

### Post by uroskriznar on 2007-11-18
Hi. I'm using Ubuntu 7.10.

I installed sun java version 1.6.0_03, because JIN chess applet is not working in firefox.
I installed it in my home folder under java.

This is the info I get in the console (everything seems O.K.):

uros6@uros6-desktop:~$ sudo java -version
[sudo] password for uros6:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
uros6@uros6-desktop:~$

But this is what I get in firefox on the Sun homepage and JIN still doesn't work:

Verifying Java Version

Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.

Does anyone know what the problem might be???

---

### Post by derby007 on 2007-11-18
I think you have to install the Java Software Developer Kit (SDK) and not just the Java Runtime Environment (JRE)

Or see thread: [http://ubuntuforums.org/showthread.php?t=588556&page=2]("http://ubuntuforums.org/showthread.php?t=588556&page=2")

---

### Post by geirha on 2007-11-18
Have you installed the **sun-java6-plugin** package? 

also, do ```
update-java-alternatives --list
``` and make sure you set the correct version with ```
sudo update-java-alternatives --set java-6-sun
```

---

### Post by uroskriznar on 2007-11-18
I used synaptic to remove the "gcjwebplugin" and all is good!

Thanks.

---

