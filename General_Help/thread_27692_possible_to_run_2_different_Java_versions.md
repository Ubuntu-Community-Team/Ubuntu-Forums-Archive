---
title: "possible to run 2 different Java versions?"
date: 2005-04-17
forum: General Help
---

### Post by gunnyman on 2005-04-17
I have Java JRE installed per the excellent ubuntuguide website.
The  plugin works nicely in Mozilla. 
I am trying to get JavaHMO installed on this system so I can feed mp3's and what not to my Tivo.  It requires 1.42 JRE.  Can I install it too? I would put it in /opt most likely.
The only issue I can't get my head around, is the program relies on the JAVA_HOME environment to be set.  It is currently set to the location of the newer Java.

The reason I can't just use 1.42 system wide, is I use a java based web chat pretty often and it just looks butt ugly with the older plugin.

Anyone been able to get Java HMO working on Hoary?

---

### Post by soul_rebel on 2005-04-18
java 1.5 should be compatible with 1.4.2 ... and you should not have any problem keeping java 1.4.2 for a while.

anyway yes, you can have a lot of jre installed, but is not that simple. 

atp sources for java:
```

deb ftp://neacm.fe.up.pt/pub/ubuntu-java/ binary/
deb-src ftp://neacm.fe.up.pt/pub/ubuntu-java/ source/
```

update-alternatives could do the trick to switch from one to the other. I can't give you an answer like "type this to do that" so you will have to read something about update alternatives.

(maybe also jpackage-utils could help)

---

### Post by gunnyman on 2005-04-18
Thanks 
I am looking at re-writing the config script that Java HMO uses to point to an alternate JRE rather than depending on JAVA_HOME.
Meanwhile I got Samba working well enough to use my wife's PC as a TiVo server.

---

### Post by soul_rebel on 2005-04-18
some programs have the possibility to set a jre. GOOD
Some just want the path to java executable.  NOT SO GOOD
some other use just "java" (hoping it's in $PATH) and don't worry. NORMAL

$JAVA_HOME and the others are used by java to find its files, not by applications.

So switching jre needs changing enviroment variables AND symlinks.

fortunately you don't need to write a script on your own, but to learn update-alternatives.

Also please post the solution here for any user in your situation.

---

### Post by gunnyman on 2005-04-20
Situation fixed!
Here's what I did.
I installed JRE 1.5 in /opt
I installed the java my application, JavaHMO needed, 1.42 in /usr/lib/java.
Luckily, the Mozilla java plugin does NOT seem to care  about JAVA_HOME being set.
So I have the plugin from JRE 1.5 working in Mozilla but java -version will give 1.42 like my beloved JavaHMO requires.
This is so awesome.  Getting mp3's and photos to my tivo from my pc was the only thing keeping from being a full time Linux user.

---

