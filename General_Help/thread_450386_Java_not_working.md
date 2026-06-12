---
title: "Java not working"
date: 2007-05-21
forum: General Help
---

### Post by ronbrooks on 2007-05-21
I can't get Java to run after upgrade to 7.04.  After looking on the forum it looks like I should have this file in my home directory libjamplugins-oji.so in the .mozilla/plugin but it is not there I do have one in my usr/lib/mozilla-firefox/plugins. It is also not in my usr/lib/mozilla/plugins.

I have tried to reinstalling it but it didn't do any good. 

Can anyone help with this trouble. I would like to get java working.  I have been working on it for two days now with no luck.

---

### Post by zvacet on 2007-05-21
[http://www.java.com/en/download/help/5000010500.xml]("http://www.java.com/en/download/help/5000010500.xml")

---

### Post by Bablefish on 2007-05-21
There is an even easier way to install Java just go to Add Remove and check under internet it's listed

---

### Post by chunchengch on 2007-05-21
Please refer to my thread "Personal summary of installing JAVA/JRE in Ubuntu 7.04", wish it will be helpful!

[http://ubuntuforums.org/showthread.php?p=2694354#post2694354](http://ubuntuforums.org/showthread.php?p=2694354#post2694354)

---

### Post by ronbrooks on 2007-05-21
Chunchengch that site is not in english so I didn't know what file to down load. 

The program is installed but I just can't get it to work. 

ronbrooks@ronbrooks-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

Each time I go to a web site with Java I keep getting a plug in needs to be added. 

This is realy getting to me.

---

### Post by mgmiller on 2007-05-27
It looks like you installed java6 for everything except your browser.

```
sudo apt-get install sun-java6-plugin
```

that should get it running.

take a look in synaptic package manager and search for sun-java6

the following should be installed:
sun-java6-bin
sun-java6-fonts
sun-java6-jre
sun-java6-plugin

---

