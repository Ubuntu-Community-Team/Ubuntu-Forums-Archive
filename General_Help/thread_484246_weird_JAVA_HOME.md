---
title: "weird JAVA_HOME"
date: 2007-06-25
forum: General Help
---

### Post by anv on 2007-06-25
I tried to run Java based software and it gave really odd looking message:

Error: JAVA_HOME is not defined correctly.
  We cannot execute /usr/bin/java/bin/java

how to set this correctly? I have already done this: export JAVA_HOME=/usr/bin/java

---

### Post by AlexThomson_NZ on 2007-06-25
Actually JAVA_HOME should point to an installed java sdk or jre directory, rather than the executable.

If you have Sun's java, point it to where it is installed (it should be something like /usr/local/j2sdk1.5.0_12 or something similar- that's where I installed mine, but yours will likely be different)

If you don't use Sun's Java, you really should install it if you are doing any serious java stuff- it's not too hard now, and there are plenty of FAQs that are pretty easy to follow to do this

---

### Post by anv on 2007-06-25
-I have Sun-Java

-correct solution, It started to run after pointing it to installed folder instead of the bin file

---

### Post by anv on 2007-06-25
second question how do I point it for my web browser?  It seems that package which I downloaded from Sun jre1.6 does not contain libjavaplugin_oji.so,

---

### Post by nicktmro on 2007-07-12
Follow these instructions and you should get a system that is able to find a proper JAVA_HOME:
[http://tmro.blogspot.com/2007/07/ubuntu-and-java-javahome-no-longer.html](http://tmro.blogspot.com/2007/07/ubuntu-and-java-javahome-no-longer.html)

Basically JAVA_HOME represents the installation directory of your JDK.

It might be useful to run a 
```
 $ java -version
```

and make sure you have the right version (if it does not find java then you have a different problem: your PATH)

Another thing worth trying is running 
```
$ whereis java
```
to find out what your PATH should look like :)

Cheers

---

