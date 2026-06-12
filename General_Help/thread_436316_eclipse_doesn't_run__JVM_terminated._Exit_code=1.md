---
title: "eclipse doesn't run : JVM terminated. Exit code=1"
date: 2007-05-07
forum: General Help
---

### Post by arsham on 2007-05-07
Hi
After searching/googling around , never found any answers , anyways...
Nobody explained what is this and the certain way to solve the problem , even removing java and eclipse didn't help

The code is here :

> JVM terminated. Exit code=1
/usr/lib/jvm/java-1.5.:confused: 0-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 261b800c
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-1.5.0-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar


I'm using ubuntu feisty
And tried several purging/installing of java,eclipse and every dependencies

Help required for continue developing

Regards
Arsham

---

### Post by mlind on 2007-05-07
Download eclipse SDK from eclipse.org and install Sun's JDK from Ubuntu repository. Although gcj is very impressive piece of software, it's not as good as Sun's. At least that's what I'm still doing and I've been using eclipse for 3 years now.

---

### Post by arsham on 2007-05-07
Thanks for reply
I did it , but the problem remains
I don't know what have I done , but it seems somethings wrong with my configuration files 
I will try as a different user and see what happens

But , I also use Zend Studio 5.5 and couple of java programs without any problem

Regards
Arsham

---

### Post by b05q on 2007-05-08
take a look at post #18 here:

[http://ubuntuforums.org/showthread.php?t=315444&page=2](http://ubuntuforums.org/showthread.php?t=315444&page=2)

---

### Post by arsham on 2007-05-08
> **b05q said:**
> take a look at post #18 here:

[http://ubuntuforums.org/showthread.php?t=315444&page=2](http://ubuntuforums.org/showthread.php?t=315444&page=2)

Didn't help
Everythings like before :(

---

### Post by mixmaster on 2007-05-08
For what it is worth, I am running the eclipse stack (I need it for native Lotus Notes).  My java version is 1.4.2.  Might you have a version mismatch?

---

### Post by mlind on 2007-05-08
Make sure you're using Sun's jvm when running elicpse. use update-jave-alternatives to switch to sun's implementation.

if you're running x64, you may need to specify -XX:MaxPermSize=128M as runtime argument (put it in eclipse.ini). This solves crashing for on 64 arch for me.

If this doesn't help any, try starting eclipse with -clean argument, or even remove .metadata folder where your workspace is located.

---

### Post by arsham on 2007-05-08
> **mlind said:**
> Make sure you're using Sun's jvm when running elicpse. use update-jave-alternatives to switch to sun's implementation.

if you're running x64, you may need to specify -XX:MaxPermSize=128M as runtime argument (put it in eclipse.ini). This solves crashing for on 64 arch for me.

If this doesn't help any, try starting eclipse with -clean argument, or even remove .metadata folder where your workspace is located.

Thanks for reply
I tried everything , also :
> 
eclipse -vm /usr/lib/jvm/java-1.5.0-sun/bin/java

and :
> 
eclipse -vm /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin/java


The problem still remains :(

these are what I have installed : 

> 
.......
ii  sun-java5-bin                              1.5.0-11-1ubuntu2                          Sun Java(TM) Runtime Environment (JRE) 5.0 (architectu
ii  sun-java5-demo                             1.5.0-11-1ubuntu2                          Sun Java(TM) Development Kit (JDK) 5.0 demos and examp
ii  sun-java5-jdk                              1.5.0-11-1ubuntu2                          Sun Java(TM) Development Kit (JDK) 5.0
ii  sun-java5-jre                              1.5.0-11-1ubuntu2                          Sun Java(TM) Runtime Environment (JRE) 5.0 (architectu
ii  sun-java5-plugin                           1.5.0-11-1ubuntu2                          The Java(TM) Plug-in, Java SE 5.0
......


---

### Post by arsham on 2007-05-08
[SOLVED]
Problem solved , but not fairly

I installed java 6 and did this :

> 
update-java-alternatives -s /usr/lib/jvm/java-6-sun


After that eclipse is running , but why with version of 6 and not with 5?

Thank you all for your help

Please keep this thread open to find a real solution , helping ubuntu to be the most user friendly distro ever
:guitar:

---

### Post by mexpolk on 2008-01-15
This is my solution, and works great:

[http://ubuntuforums.org/showthread.php?p=4141441]("http://ubuntuforums.org/showthread.php?p=4141441")

Best

---

### Post by mexpolk on 2008-01-16
Last update of my solution...

[http://ubuntuforums.org/showthread.php?p=4141478#post4141478]("http://ubuntuforums.org/showthread.php?p=4141478#post4141478")

---

