---
title: "System Freeze by Java programs?"
date: 2013-03-25
forum: General Help
---

### Post by kleinempfaenger on 2013-03-25
Hi, 
I have experienced several system freezes since last week (Ubuntu 12.10). They occur during activities in Java programs, like Mozilla, Thunderbird, DraftSight. For example: scrolling down a page in Mozilla causes freeze. Some seconds later an advice, that a problem occured, or total system freeze. 
Advice: "Apport has detected a possible GPU hang.  Did your system recently lock up and/or require a hard reboot?" Afterwards several error messages.
Is there any information about a bug in Java or something like this? I have updated the system, but freezes still occur.
Any advice or help, that I could follow?

Greetings, kl

---

### Post by 0xc0de on 2013-03-25
Hello! What version of Java you use?
You can try Oracle Java or Openjdk (6, 7).

---

### Post by kleinempfaenger on 2013-03-25
I think it is Openjdk. I have 6 an d 7 installed. I dont know if I have Sun Java installed. As far as I know I dont have it. How do I install it and how could I link my programs to run with it?

---

### Post by 0xc0de on 2013-03-25
You can what version of OpenJDK installed by running
```
dpkg --get-selections | grep openjdk
```
You can also try to reinstall openjdk or replace openjdk (by deleting openjdk and installing Oracle java :) ) with Oracle Java (can be downloaded from [java.com]("https://www.java.com/en/download/manual.jsp?locale=en#lin") or check out [this guide]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html"))

---

### Post by kleinempfaenger on 2013-03-25
This is what it told me. I think it is both installed. Could that cause conflicts?

openjdk-6-jdk:amd64                install
openjdk-6-jre:amd64                install
openjdk-6-jre-headless:amd64            install
openjdk-6-jre-lib                install
openjdk-7-doc                    install
openjdk-7-jdk:amd64                install
openjdk-7-jre:amd64                install
openjdk-7-jre-headless:amd64            install
openjdk-7-jre-lib                install

I would give it a try with Oracle Java. Do you recommend that? It looks like a workaround, as there are only rpm-packages available. Thanks.

---

### Post by neo1691 on 2013-04-03
I am having exactly the same problem and the problem arised when I was working with netbeans IDE. The error is popping up frequently. Any help on this?

---

### Post by kleinempfaenger on 2013-04-08
Ok, after sun java install system wouldnt freeze, but sometimes errors pop up. Did the following:


[COLOR=#c20cb9]**sudo**[/COLOR] add-apt-repository ppa:webupd8team[COLOR=#000000]**/**[/COLOR]java [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get update**[/COLOR] [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get install**[/COLOR] oracle-java7-installer

Afterwards uninstalled openjdk. Minecraft wouldnt work any more, so be carefull to meet your children afterwards.

---

