---
title: "Java Installation Problems"
date: 2017-03-09
forum: General Help
---

### Post by cole7 on 2017-03-09
Hi.  
Hoping someone can help me out.  I am using Ubuntu 14.04 LTS and I am trying to install some software via the terminal.  When I try to install I get the following:

Configuring the installer...
Searching for JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 7 is required for installing myDESIGNER. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.


But when I run java -version I get:
java version "1.7.0_80"
Java(TM) SE Runtime Environment (build 1.7.0_80-b15)
Java HotSpot(TM) 64-Bit Server VM (build 24.80-b11, mixed mode)

Which leads me to believe that I installed JDK correctly. 
The next thing that I thought I messed up was I didn’t assign a home path but when I run echo $JAVA_HOME i get the following:

/usr/lib/jvm/java-7-oracle

So as far as I can tell I have done everything correct.  What am I missing?????

Thank You

---

### Post by QIII on 2017-03-09
What you have there is an indication that the JVM is installed.   The JDK is another matter.

To make sure everything is cleanly installed, I highly recommend following the very easy instructions [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") to get Java 8.

You need only run three commands, as the scripts take care of everything for you:

```
sudo add-apt-repository ppa:webupd8team/java
```
```
sudo apt-get update
```
```
sudo apt-get install oracle-java8-installer
```

Please read the section titled **"Update October 20, 2016:"**

---

### Post by cole7 on 2017-03-09
QIII
Thank You.  Finally got it installed.:D:D

---

