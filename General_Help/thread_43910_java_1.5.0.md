---
title: "java 1.5.0"
date: 2005-06-23
forum: General Help
---

### Post by mailophobic on 2005-06-23
where do i add the path to javac, java... is it in .bashrc, .bash_profile? 

thanks in advance

---

### Post by DJ_Max on 2005-06-24
.bash_profile is your user profile. .bash is globally. So either one will do.

---

### Post by mailophobic on 2005-06-28
im still having trouble using the javac and java commands, my path addition isnt  working anyone has some clue what to add to the file?

---

### Post by Leif on 2005-06-28
Why don't you simply apt-get it ? Then everything is setup for you

---

### Post by amerigo5 on 2005-06-28
Starter Guide for 4.10 has a good reference for this - [http://ubuntuguide.org/4.10/index.html#jre](http://ubuntuguide.org/4.10/index.html#jre)

$ sh jdk-1_5_0_04-linux-i586.bin
$ sudo mkdir /usr/java
$ sudo mv jdk1.5.0_04/ /usr/java/
$ sudo chown -R root:root /usr/java/jdk1.5.0_04/
$ sudo ln -s /usr/java/jdk1.5.0_04/bin/java /usr/bin/java
$ sudo gedit /etc/bash.bashrc

Append the following:

JAVA_HOME=/usr/java/jdk1.5.0_04
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

---

### Post by noodle on 2005-06-28
If you have to logout and in again before changes made to your .bashrc file will take effect.

---

### Post by mailophobic on 2005-07-06
thanks for the help, i must have missed it in the guide. And i cant apt-get it i dont have an internet connection at home.

---

### Post by noodle on 2005-07-15
Have you got Java Runtime Enviroment and the Java Software Development Kit installled?

If you do, in your .bashrc file, point to the path of your java SDK installation file, 

e.g.

```
export JAVA_HOME=/usr/lib/j2sdk1.5-sun/
```

You have to save, logout and back in again before changes to the .bashrc file take effect.

You can verify that is working corectly, by checking that you get a response when typing in terminal:
```

java -version 
javac -help
```

---

