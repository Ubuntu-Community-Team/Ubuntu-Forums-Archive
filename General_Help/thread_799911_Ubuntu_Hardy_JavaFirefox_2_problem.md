---
title: "Ubuntu Hardy Java/Firefox 2 problem"
date: 2008-05-19
forum: General Help
---

### Post by Kreuger on 2008-05-19
Hey people, been having trouble getting java to work in Hardy with Firefox 2 (which I need for my plugins). I've seen a few pages on Google about this and most of them suggest removing and reconfiguring (as well as selecting the right one with the alternatives selection tool) and I've tried this to no avail. I have sun-java6-bin, sun-java6-jre, sun-java6-plugin installed. I had sun-java5 for each of them installed and they didnt work. I had the OpenJDK installed and that didnt work. I had Iced Tea installed and that didnt work. I'm really at a loss here. I've got the java file linked into my Firefox plugins directory but it doesn't show up when I use "about: plugins" (I spaced here to remove the smiley). I grabbed the installer off their site and installed 1.6.0_05 into /usr/java and that also did nothing. I can use Frostwire just fine though so I don't get it.

> kreuger@kreuger-desktop:~$ whereis java
java: /usr/bin/java /etc/java /usr/lib/java /usr/share/java

> kreuger@kreuger-desktop:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

---

### Post by drs305 on 2008-05-19
Have you tried uninstalling all java variations and then reinstalling? Sometimes there are conflicts or residuals that keep java from working properly.

If you have a 32 bit system,
```
sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get  install sun-java6-fonts sun-java6-jre sun-java6-plugin 
```

Rereading your post, you might even want to break the commands up into two parts. Remove java, then get into synaptic, do a search for java, and make sure nothing is listed as installed, and then running the second half.

---

### Post by Kreuger on 2008-05-19
Well I already tried removing everything in Synaptic and reinstalling it there afterwards (that was using complete removal). It has brought me to where I am now (before that when I ran java -version it said I didnt have java installed)

---

