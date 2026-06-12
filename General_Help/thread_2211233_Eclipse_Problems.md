---
title: "Eclipse Problems"
date: 2014-03-15
forum: General Help
---

### Post by Robert_Hubbard on 2014-03-15
Hi, I am new to this forum and Ubuntu.  I am not sure if this is the correct place for this thread but here goes.  I have been trying to get eclipse kepler on my Ubuntu 13.10.  I am pretty sure i have installed it correctly but when I try to open eclipse in my terminal I get this message.  Any help would be greatly appreciated.  I am a student and need eclipse so I can write projects in C++.  The message is: 

```
Java HotSpot(TM) 64-Bit Server VM warning: You have loaded library /opt/64/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.200.v20140116-2212/eclipse_1508.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
Eclipse:
JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.6
-XX:MaxPermSize=256m
-Xms40m
-Xmx512m
-jar /opt/64/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.v20130327-1440.jar
-os linux
-ws gtk
-arch x86
-showsplash /opt/64/eclipse//plugins/org.eclipse.platform_4.3.2.v20140221-1700/splash.bmp
-launcher /opt/64/eclipse/eclipse
-name Eclipse
--launcher.library /opt/64/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.200.v20140116-2212/eclipse_1508.so
-startup /opt/64/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.v20130327-1440.jar
--launcher.appendVmargs
-exitdata 173000b
-product org.eclipse.epp.package.cpp.product
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.6
-XX:MaxPermSize=256m
-Xms40m
-Xmx512m
-jar /opt/64/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.v20130327-1440.jar 
```

Thanks again.

---

### Post by samwillc on 2014-03-15
I know this is not a specific fix for you, but may help.

I have eclipse keplar working fine in eOS which is based on ubuntu 12.04 LTS. I downloaded from eclipse website rather than software centre, moved it to /opt and created a .desktop file. I also use jdk rather than openjdk:

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

```

I never needed java v1.6 for this to work.

```

sam@sam-pc:~$ java -version
java version "1.7.0_51"
Java(TM) SE Runtime Environment (build 1.7.0_51-b13)
Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode)
sam@sam-pc:~$ 

```

In the meantime, you could try code:blocks for C++, it's available in  the software centre (I am a student too and deadlines don't wait for you to fix a program!). At least this way you can get on with your work  while you get eclipse working/wait for other replies.

Sam.

---

### Post by Robert_Hubbard on 2014-03-15
Thank you for the reply. I may just remove eclipse and start all over again.  I tried installing the java you had provided but the same error is displayed.  Thank you.

---

### Post by samwillc on 2014-03-16
I just found this in my bookmarks and thought this may help you:

[http://askubuntu.com/questions/337281/installing-eclipse-kepler-and-java-jdk](http://askubuntu.com/questions/337281/installing-eclipse-kepler-and-java-jdk)

Good luck :)

---

