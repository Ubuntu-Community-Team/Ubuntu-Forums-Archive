---
title: "Java question"
date: 2008-02-07
forum: General Help
---

### Post by Bablefish on 2008-02-07
I just like a straight answer to a straight forward question. 

I used everything everybody suggested and I have Java 6 installed. But when I went to about:plugins on Firefox to see what version of Flash I had installed. It said my default was Java 1.6 and when I went to the Java test page it said I was using Java 1.4. 

I know and have used  

sudo update-alternatives --config java

It says I have Java 6 as my default.

What is the hell is going on?!!!!!!!!!!!

---

### Post by taurus on 2008-02-07
Can you post the output of these commands from a terminal?

```
java -version
sudo update-alternatives --config java
```

---

### Post by Bablefish on 2008-02-07
user@user-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
user@user-laptop:~$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.

and when after I did what you see I ran Java -version once again and I still got the same info.

---

### Post by taurus on 2008-02-07
Which java test site did you visit?

---

