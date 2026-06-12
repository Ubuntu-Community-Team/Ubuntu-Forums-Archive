---
title: "Chrome for java"
date: 2018-12-08
forum: General Help
---

### Post by GirishSharma on 2018-12-08
I having below environment :


girish@gk:~$ java -version
openjdk version "10.0.2" 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.4)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.4, mixed mode)


girish@gk:~$ which java
/usr/bin/java
girish@gk:~$ 


Google Chrome Version : Version 71.0.3578.80 (Official Build) (64-bit)


Also have /usr/java/jdk1.8.0_191


I need to enable java in chrome to run java applet for Netbean 8.2. When I [https://www.java.com/en/download/installed.jsp](https://www.java.com/en/download/installed.jsp)
to check Java version, it do not confirm the java working in chrome browser. Kindly help me.

---

### Post by Holger_Gehrke on 2018-12-08
[https://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html](https://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html)

Chrome does not support the API needed for the Java Plugin any more and neither does Firefox. Applets are only a historical curiosity today. If you have old applets that you want to take a look at, there's a program called appletviewer included with the JDK but you really should not even try to develop new applets because nobody could normally run them.

Holger

---

### Post by GirishSharma on 2018-12-09
> **Holger_Gehrke said:**
> [https://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html](https://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html)

Chrome does not support the API needed for the Java Plugin any more and neither does Firefox. Applets are only a historical curiosity today. If you have old applets that you want to take a look at, there's a program called appletviewer included with the JDK but you really should not even try to develop new applets because nobody could normally run them.

Holger
As you said "but you really should not even try to develop new applets because nobody could normally run them." Then what should I learn/try
to develop database web apps? Which is recommended technology/tools for Ubuntu which have drag and drop controls IDEs. Since, I am having
.NET exposure, so I tried with Monodevelop too, but that do not provide me drag and drop feature for faster development, so I moved to Netbeans and integrated applet into .jsp or html. Kindly suggest your thoughts.

---

