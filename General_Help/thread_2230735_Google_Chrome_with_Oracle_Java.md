---
title: "Google Chrome with Oracle Java"
date: 2014-06-20
forum: General Help
---

### Post by Bigpat on 2014-06-20
Hello all I'm hoping that someone can help me with Orcle Java installation for google Chrome. I'm Unable to verify Java installation in Google Chrome after createing a symbolink. Whenever I go to the test page it keeps asking for pluging.I'm using Ubuntu 14.04 LTS 32 bit with a fresh install. Also, please note that I'm using orcle Java 8 and I have tried 7 and I still have the same issue. Java varify in Fire Fox but not Google Chrome. I have used the commands below and it created the folder and also copied the required file to that folder.

This is a fresh install of 14.04 32bit.

patrick@Wheezy:~$ java -version
java version "1.8.0_05"
Java(TM) SE Runtime Environment (build 1.8.0_05-b13)
Java HotSpot(TM) Server VM (build 25.5-b02, mixed mode)

and these are the commands I used for the symbolic link

patrick@Wheezy:~$ sudo  cd /opt/google/chrome/plugins
[sudo] password for patrick: 
root@Wheezy:~#  cd /opt/google/chrome/plugins
root@Wheezy:/opt/google/chrome/plugins# ln -s /usr/lib/jvm/java-8-oracle/jre/lib/i386/libnpjp2.so


Thanks in Advance for Any help to resolved this issue.

---

