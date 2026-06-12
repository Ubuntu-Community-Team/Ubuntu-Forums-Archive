---
title: "Gay.com Chat, Java, and Automatix Issue"
date: 2007-08-05
forum: General Help
---

### Post by akarimco on 2007-08-05
OK, so there has been a lot of talk recently about how harmful Automatix is to your system, and thanks to some other detrimental crap I've done, I'll probably be reinstalling Ubuntu soon.  The problem is that I frequent the chat rooms on Gay.com (be nice!), and they run on Java.  Now, when I install Java through Add/Remove Programs or Synaptic, I have issues with the chat rooms where everything works until I get to where I click on a specific room and then nothing ever happens.  On the other hand, when I install Java through Automatix, the room pops up and it works perfectly.  I was wondering if someone a little more savvy than myself could figure out what Automatix is doing differently so that perhaps I can just do that myself and avoid Automatix altogether... without any help, I'll be stuck using it again once I reformat and start all over.

---

### Post by apswartz on 2007-08-05
If its working I'd stick with it.

---

### Post by akarimco on 2007-08-05
Oh I know, but I'd hate to install Automatix on a clean system... even if all I install is Java, I have this feeling that Automatix is doing other nasty things behind the scenes, and the whole reason I'm gonna reformat in the first place is because I'm kinda obsessive-compulsive about extraneous stuff on my system, so I'd rather avoid it if at all possible.

---

### Post by aysiu on 2007-08-05
All Automatix does, according to its source code, is ```
sudo apt-get --assume-yes install sun-java6-jre sun-java6-bin sun-java6-plugin
sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
``` for Sun Java JRE **or** ```
sudo apt-get --assume-yes install sun-java6-jdk
``` for Sun Java JDK.

---

### Post by akarimco on 2007-08-05
Hmm, perhaps it could be caused by my confusion over Java 5 and Java 6, cuz hell if I know the difference... perhaps I'll just try installing all of the Java 6 stuff and leave 5 alone.

---

