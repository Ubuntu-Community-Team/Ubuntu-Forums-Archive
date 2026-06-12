---
title: "Java Firefox plugin on Ubuntu 14.04"
date: 2016-11-25
forum: General Help
---

### Post by prkos on 2016-11-25
The plugin asked to be updated, and led to Oracle page about updating entire java to a newer version, which I did. 

But the plugin still says it's outdated. 

```

$ java -version
java version "1.8.0_111"
Java(TM) SE Runtime Environment (build 1.8.0_111-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.111-b14, mixed mode)

```
It's installed into /usr/lib/jvm/jre1.8.0_111 but the Plugin says  /usr/lib/jvm/java-8-oracle/ 

```

Java(TM) Plug-in 11.11.2

    File: libnpjp2.so
    Path: /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnpjp2.so
    Version: 11.11.2
    State: Disabled (STATE_VULNERABLE_UPDATE_AVAILABLE)
    Next Generation Java Plug-in 11.11.2 for Mozilla browsers

```

How do I tell Firefox to look in the right location? I asked about it on Mozillazine and was told it may be Ubuntu specific.

---

### Post by QIII on 2016-11-25
The easiest way to make sure Oracle Java and the Java browser plugin are installed where Ubuntu expects them to be is by following the instructions [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").  

There are three commands to run in the terminal

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

### Post by engine on 2016-11-26
That looks promising as an answer to a question I'm struggling with &#8210; do these apparently simple instructions also apply to 16.0.4?

---

