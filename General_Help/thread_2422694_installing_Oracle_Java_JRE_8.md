---
title: "installing Oracle Java JRE 8"
date: 2019-07-11
forum: General Help
---

### Post by bobptz on 2019-07-11
Hello

I have downloaded and extracted this file:  jre-8u211-linux-x64.tar.gz

Now I have a directory named, and this has some subdirectories :
jre1.8.0_211

It has several subdirectories.

As I understand Java is not working.  What else am I supposed to do?

I am lost.  I spent all day trying to setup oracle java 11 and have settled for ver 8.

---

### Post by dragonfly41 on 2019-07-11
Run the command

```
echo $JAVA_HOME
```

If there is no return then you have no previous java installations.

Now you need to set $JAVA_HOME and I choose to set this in ~/.profile (a hidden file).
If you have saved your jre1.8.0_211 in say /opt/jre1.8.0_211

you write in ~/.profile the line

```
 export JAVA_HOME=/opt/jre1.8.0_212/jre/bin
``` (i.e. the path to java executable)

you might have to check/tweak that path since I'm looking at jdk installation.
Then logout/login or reboot to update environment and again check echo $JAVA_HOME in terminal.

Also in terminal run command ```
java --version
```

---

