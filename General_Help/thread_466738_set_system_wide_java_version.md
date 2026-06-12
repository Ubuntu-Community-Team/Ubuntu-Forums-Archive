---
title: "set system wide java version"
date: 2007-06-07
forum: General Help
---

### Post by mrynit on 2007-06-07
im am trying to run eclipse but it is running insanely slow. I installed it via apt-get and the version is the newest one 3.2.2. I talked to some people in #eclipse about this and they said it was probably because eclipse was running in the wrong version of java vm. so my problem is figuring out what version of java it is truely using and how to change it. from terminal i have test the below

```
christopher@ubuntu:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

```
christopher@ubuntu:~$ javac -version
javac 1.6.0

```

woo woo thats the right version of java! but wait lets check eclipse

really long here
```
/usr/lib/jvm/java-gcj/bin/java
...
eclipse.vm=/usr/lib/jvm/java-gcj/bin/java
eclipse.vmargs=-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
...
gnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
gnu.gcj.progname=/usr/lib/eclipse/startup.jar
gnu.gcj.runtime.VMClassLoader.library_control=never
gnu.gcj.runtime.endorsed.dirs=/usr/share/java/gcj-endorsed
...
http.agent=gnu-classpath/0.92 (libgcj/4.1.2 (Ubuntu 4.1.2-0ubuntu5))
java.class.path=/usr/lib/eclipse/startup.jar
...
java.library.path=/usr/lib/jni
java.runtime.version=1.4.2
java.specification.name=Java(tm) Platform API Specification
java.specification.vendor=Sun Microsystems Inc.
java.specification.version=1.4
java.vendor=Free Software Foundation, Inc.
java.vendor.url=http://gcc.gnu.org/java/
java.version=1.4.2
java.vm.info=GNU libgcj 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
java.vm.name=GNU libgcj
java.vm.specification.name=Java(tm) Virtual Machine Specification
java.vm.specification.vendor=Sun Microsystems Inc.
java.vm.specification.version=1.0
java.vm.vendor=Free Software Foundation, Inc.
java.vm.version=4.1.2 (Ubuntu 4.1.2-0ubuntu5)
```

is eclipse running 4.1.2 or gcj, only gcj??? lets do some more probing
```
christopher@ubuntu:~$ update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/jvm/java-gcj/jre/bin/java
*         3    /usr/lib/jvm/java-6-sun/jre/bin/java

```
i did more checking and gcj has priority 1041 java6 has 63.
ok so my defualt is java 6 but priority is set to gcj. so am i running in java 6 or gcj!?!

I ran this in eclipse
```
System.out.println(System.getProperty("java.version"));  
System.out.println(System.getProperty("java.vm.version")); 
```

output
```
1.6.0
1.6.0-b105
```

eclipse is running in java6?? but it is really slow. the people in #eclipse said i might be gcj. i asked in #java and they said it was gcj. but from the above i have no idea which i am running eclipse in.

so how do i run eclipse on ubunut not slow? is this the longest post?

---

### Post by NeoLithium on 2007-06-07
Take a peek here: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Java_Integrated_Development_Environment_.28Eclipse.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Java_Integrated_Development_Environment_.28Eclipse.29)
It was written for Edgy, however there shouldn' t be any problems using the instructions to switch over java for it to run better.

---

### Post by NeoLithium on 2007-06-07
Ok, I tested this out on my own (Since i haven't run eclipse.)  The way I got it to work, was to open up eclipse, move to preferences, and go to Window -> Preferences -> Java. Then go to Installed JREs  and Add a new one. Name the JRE what you like. I just named mine Sun-Java-6 and for the home directory use /usr/lib/jvm/java-6-sun/ and click ok.

---

### Post by ditsch on 2007-06-07
The trick is setting the VM in /etc/eclipse/java_home. The settings in Eclipse itself only configure which VM to compile files against. Therefore you get a different output from System.getProperty in a java file running from eclipse depending on the eclipse settings.

---

### Post by mrynit on 2007-06-07
your link fixed it. all i had to do was edit the java home file
```
gksudo gedit /etc/eclipse/java_home
```

your second post is about the JRE eclipse uses to run your programs not the JRE eclipse uses to run itself.

thanks for the help. really simple fix.

---

