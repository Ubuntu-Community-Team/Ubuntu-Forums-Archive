---
title: "Installing Oracle Java plugin Firefox"
date: 2013-12-28
forum: General Help
---

### Post by e1ektrob0y on 2013-12-28
I followed this [http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux"). Java seems to be installed ```
ben@ben:~$ java -version
java version "1.7.0_45"
Java(TM) SE Runtime Environment (build 1.7.0_45-b18)
Java HotSpot(TM) 64-Bit Server VM (build 24.45-b08, mixed mode)
```
```
ben@ben:~$ javac -version 
javac 1.7.0_45
```
The how to guide says to create a symbolic link to the file libnpjp2.so. The only problem is that file does not seem to exist in the directory /usr/local/java/jre1.7.0_40/lib/amd64/. Instead there is another folder called /jli which contains the file libjli.so. When i create a symbolic link to that file in usr/local/mozilla/plugins java java does not then work in firefox. 

What have i done wrong?

---

### Post by QIII on 2013-12-28
Hello!

By far, the easiest way to install Oracle Java 7 is to use the instructions[ here]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html").  Everything else is just too difficult.

It takes care of everything for you, including automatic updates as Oracle releases them.

---

### Post by e1ektrob0y on 2013-12-28
Thanks. I found the file. It was in /usr/local/java/jdk1.7.0_45/jre/lib/amd64/ not /usr/local/java/jre1.7.0_45/lib/amd64/ which is what the tutorial says. Maybe its a typo? Anyway...It works now :)

---

