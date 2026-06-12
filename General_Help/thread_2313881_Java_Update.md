---
title: "Java Update"
date: 2016-02-16
forum: General Help
---

### Post by feartheterrapin on 2016-02-16
When will webupd8 update java?
 
 I use webupd8 ppa to keep my java updated.  I never pay attention to the latency of when webupd8 provides an update.  I noticed earlier this week that Firefox says my java is outdated.
 ```
Java Runtime Environment
  Next Generation Java Plug-in 11.72.2 for Mozilla browsers outdated
 8.0.72

``` 
 My current java configuration is as follows:
 ```
~$ java -version
  java version "1.8.0_72"
 Java(TM) SE Runtime Environment (build 1.8.0_72-b15)
 Java HotSpot(TM) 64-Bit Server VM (build 25.72-b15, mixed mode)
  
 ~$ dpkg -l | grep openjdk
 ii  openjdk-7-jre                                 7u95-2.6.4-0ubuntu0.12.04.1             OpenJDK Java runtime, using Hotspot JIT
 ii  openjdk-7-jre-headless                        7u95-2.6.4-0ubuntu0.12.04.1             OpenJDK Java runtime, using Hotspot JIT (headless)
  
 ~$ dpkg -l | grep openjdk
 ii  openjdk-7-jre                                 7u95-2.6.4-0ubuntu0.12.04.1             OpenJDK Java runtime, using Hotspot JIT
 ii  openjdk-7-jre-headless                        7u95-2.6.4-0ubuntu0.12.04.1             OpenJDK Java runtime, using Hotspot JIT (headless)
  
 ~$ dpkg -l | grep oracle-java
 ii  oracle-java8-installer                        8u72+8u71arm-1~webupd8~0                Oracle Java(TM) Development Kit (JDK) 8
 ii  oracle-java8-set-default                      8u72+8u71arm-1~webupd8~0                Set Oracle JDK 8 as default Java

``` 
 
 Looking at [launchpad]("https://launchpad.net/~webupd8team/+archive/ubuntu/java"), it seems  webupd8 does not have an update yet.  Do I just need to be patient or is something wrong?

---

### Post by QIII on 2016-02-16
Be patient.  webupd8 has been a one man show for several years now - one very busy man.

---

### Post by feartheterrapin on 2016-02-16
Thanks for confirming.  I can be very patient for the excellent service webupd8 provides.

---

### Post by feartheterrapin on 2016-03-02
Update came today!

---

