---
title: "How do I purge Java7 and install older version"
date: 2014-02-08
forum: General Help
---

### Post by SuperFreak on 2014-02-08
I installed Oracle Java 7 according to [THIS]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") and found it didn't work with the web based software(chat room) I was using because of some glitch it needed an older version. I removed the PPA and did this:

I```
david@MainSqueeze:~$ sudo apt-get remove oracle-java7-installer
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package oracle-java7-installer
david@MainSqueeze:~$ java -version
java version "1.7.0_51"
Java(TM) SE Runtime Environment (build 1.7.0_51-b13)
Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode)

```


As you can see from above Java7 is still installed. I can't find it in synaptic, tried the above command with purge instead of remove and it is still there according to Java -version. How do I get rid of it and go to an earlier version of Java?

edit: not sure if this was correct procedure but I deleted the java7 files/folder in /usr/lib/jvm and java seems to be gone

---

