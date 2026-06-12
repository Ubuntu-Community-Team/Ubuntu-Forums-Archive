---
title: "Adding java to bash.bashrc problem"
date: 2005-10-10
forum: General Help
---

### Post by brim4brim on 2005-10-10
Hi all,

I'm starting my 4th year project using Ubuntu (hooray) with Java and the eclipse IDE.  I have everything running after installing the JDK1.5 for eclipse and eclipse works fine (except it demands to be run using sudo).  Anyway when I go to run an exported .jar file I have to add:

JAVA_HOME=/usr/Java/jdk1.5.0_05/jre
export JAVA_HOME
PATH=$path:$JAVA_HOME/bin
export PATH

fine I save the bash.bashrc file and the bashing thing no longer allows me to run commands such as ls or access man or anything like that.  It returns to normal once I remove these lines so my question is what on earth am I doing wrong?

Oh and if anyone knows why can't I run eclipse without sudo and why does gksudo not allow extra initialisation commands at the end like -vm /usr/Java/jdk1.5.0.0_05/bin/java.  The only way I've manged to create my my custom launcher is to just use regular sudo and tell it to run in terminal.

Any help appreciated.

---

### Post by sanjose on 2005-10-10
PATH=$path:$JAVA_HOME/bin

change:

PATH=$PATH:$JAVA_HOME/bin

---

### Post by mlomker on 2005-10-10
> 
JAVA_HOME=/usr/Java/jdk1.5.0_05/jre
export JAVA_HOME
PATH=$path:$JAVA_HOME/bin
export PATH


Try:

```

export JAVA_HOME=/usr/Java/jdk1.5.0_05/jre
export PATH=$PATH:$JAVA_HOME/bin

```

---

### Post by brim4brim on 2005-10-10
[QUOTE=sanjose]PATH=$path:$JAVA_HOME/bin

change:

PATH=$PATH:$JAVA_HOME/bin[/QUOTE]

That worked thanks

---

