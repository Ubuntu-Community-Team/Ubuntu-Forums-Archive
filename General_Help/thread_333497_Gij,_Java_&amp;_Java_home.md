---
title: "Gij, Java &amp; Java_home"
date: 2007-01-07
forum: General Help
---

### Post by andrem on 2007-01-07
Hi all!

I'm having a problem with my java programs. 
Some (like Geronimo APPServer) have startup scripts that expect you to have a java environment set up. I have jdk1.6.0 installed under /opt/jdk1.6.0/ and "echo $JAVA_HOME" returns: "/opt/jdk1.6.0/". Even though, when I type "java" I get an answer from "gij", instead of SUN's java. I believe this is causing the problems, as the scripts will be answered by gij instead of SUN's Java. :confused: 

How can I change this?

Thanks in advance!

---

### Post by taurus on 2007-01-07
Applications -> Accessories -> Terminal
```
sudo update-alternatives --config java
```
And pick the one in /opt/jdk1.6.0 as your default.

---

### Post by andrem on 2007-01-07
Thanks!

I did that and I got this:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/bin/gij-wrapper-4.1
*         2    /opt/jdk1.6.0/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/opt/jdk1.6.0/bin/java' to provide `java'.

I chose the second, but now when I type "java" I get a "command not found" error, even though "java" is at that dir. Worse, if I change back to choice 1, gij no longer answers...

---

### Post by taurus on 2007-01-07
You can't even run this from a terminal!

```
/opt/jdk1.6.0/bin/java -version
```
Are you using Dapper or Edgy (x32 or x64)?

---

### Post by andrem on 2007-01-07
I can do that!

XX@YY:~$ /opt/jdk1.6.0/bin/java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

It's the java command that isn't working.

XX@YY:~$ java -version
bash: java: command not found

Shouldn't it be after setting that alternative?

(I'm using Edgy on x32)

---

### Post by taurus on 2007-01-07
Try this.

```
sudo ln -s /opt/jdk1.6.0/bin/java  /usr/bin/java
source ~/.bashrc
java -version
```

---

### Post by andrem on 2007-01-07
No, that didn't work either...

Could I have done anything wrong? Cause I still have gij-wrapper working if I set the full path to it, but if I choose it as my alternative for java, it no longer responds.

---

### Post by taurus on 2007-01-07
What's the output of this command?

```
whereis java
```

---

### Post by andrem on 2007-01-07
Here it is:

```
 whereis java
java: /usr/bin/java /usr/lib/java /usr/X11R6/bin/java /usr/bin/X11/java /usr/share/java /opt/jdk1.6.0/bin/java /usr/share/man/man1/java.1.gz

```

---

### Post by taurus on 2007-01-07
```
ls -la /usr/bin/java
```

---

### Post by andrem on 2007-01-07
```
ls -la /usr/bin/java
lrwxrwxrwx 1 root root 18 2007-01-07 20:17 /usr/bin/java -> /opt/jdk1.6.0/bin/

```

---

### Post by taurus on 2007-01-07
```
sudo rm /usr/bin/java
sudo  ln  -s  /opt/jdk1.6.0/bin/java  /usr/bin/java
```
Then, log out and back in again.

```
java -version
```

---

### Post by andrem on 2007-01-07
java -version is definatelly running now!

Thanks a lot on this help. I'll investigate on my own the ln command, since I'm quite new to linux and I think that did the trick. :D

---

### Post by taurus on 2007-01-07
That command, ln, is a linker between files.  Since you install java on /opt/jdk1.6.0/bin/java, you can copy it over to /usr/bin but that would take up some space.  Therefore, why not link the version in /usr/bin/ to where it actually is, /opt/jdk1.6.0/bin/java.  So technically, when you type "java" from a prompt, the one in /usr/bin/java will "point" you to /opt/jdk1.6.0/bin/java.  Otherwise, you just have to put /opt/jdk1.6.0/bin on your path so programs can find it.

```
man ln
```

---

### Post by andrem on 2007-01-07
I got it! I would try to change the path, but it's always useful to know 2 solutions to the same problem! ;)

---

### Post by taurus on 2007-01-07
Yes, there are ways to achieve the same result in Linux and as long as you're happy and with that method and it works, go for it.  ;)

---

