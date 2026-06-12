---
title: "jedit on ubuntu 8.04"
date: 2008-06-12
forum: General Help
---

### Post by matt_wood87 on 2008-06-12
Hi all,
i'm having trouble running jedit since i upgraded to ubuntu 8.04 from the previous version.

when i type jedit into a terminal i get the message
exec: 8: /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/bin/java: not found

when i type java -version
java version "1.5.0"

when i type which jedit
/home/matthew/bin/jedit

any help as to why it wont run would be much appreciated!

thanks

Matt

---

### Post by Titan8990 on 2008-06-12
It is actually **g**edit.

Nvm, I see that there is a seperate editor called jedit. I checked and it looks like there is no .deb package for it. Are you compiling from source?

---

### Post by matt_wood87 on 2008-06-12
no, I'm not referring to gedit [http://www.gnome.org/projects/gedit/](http://www.gnome.org/projects/gedit/), I'm referring to jedit [http://www.jedit.org/](http://www.jedit.org/), it is a different program.

thanks for looking anyway!

Matt

---

### Post by matt_wood87 on 2008-06-12
I installed it from the Synaptic Package Manager, i think when i installed it on the previous version of ubuntu i had to do it from source.

---

### Post by Titan8990 on 2008-06-12
Yeh, I was a bit late to realize that. I had another look at that jedit site and it looks like you need development version of java installed. Check to make sure you have the the JDK version of java installed.

---

### Post by matt_wood87 on 2008-06-12
in the package manager sun-java6-jdk and sun-java-jre are both installed.

---

### Post by x1a4 on 2008-06-12
Hi,

I had the same problem when I first upgraded.  I installed jEdit from source on Gutsy.   The reason this happens is that the location of Java has changed.  Simply set the JAVA_HOME environment variable to the location of Java. Or, you can remove jEdit and install it from the repos.

---

### Post by Elegorod on 2008-06-12
> The reason this happens is that the location of Java has changed.
Yes, surely.
jedit executable is actually a shell script. So, locate it
```
which jedit
```
I got /usr/local/bin/jedit
And edit this file as root
```
gedit /usr/local/bin/jedit
```
Set DEFAULT_JAVA_HOME="/usr/lib/jvm/java-6-sun/jre" to actual Java path

---

### Post by matt_wood87 on 2008-06-12
yep, thats fixed it guys! thanks very much for the help!

Matt

---

