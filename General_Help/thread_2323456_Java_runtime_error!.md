---
title: "Java runtime error!"
date: 2016-05-05
forum: General Help
---

### Post by CCgirl6690 on 2016-05-05
Hello
I'm trying to run an application and i get this error ...
```
~$ webcamstudio
[warning] /usr/bin/webcamstudio: No JAVA_CMD set for run_java, falling back to JAVA_CMD = java
Exception in thread "main" java.lang.UnsupportedClassVersionError: webcamstudio/WebcamStudio : Unsupported major.minor version 52.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:803)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:449)
    at java.net.URLClassLoader.access$100(URLClassLoader.java:71)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:361)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:425)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:358)
    at sun.launcher.LauncherHelper.checkAndLoadMain(LauncherHelper.java:482)
```
How can i fix it?
Thank you so much
---------------------------------------------That was part  1 
----------------------------------------------
If you can't help with this please try my other issue...[URL="http://ubuntuforums.org/showthread.php?t=2323456"]http://ubuntuforums.org/showthread.php?t=2323456    
Thanks
[/URL]

---

### Post by QIII on 2016-05-05
Hello!

I have modified the title of your thread.  A meaningful title rather than something generic like "Help me!" is more likely to get the attention of those who can help.

Also, I ***highly recommend*** that you edit out the second part of your post and create a new thread for that question.  It becomes very confusing very quickly when a lot of different people are trying to answer more than one question in a thread.  As a rule, please keep each thread to a single issue.

Cheers!

---

### Post by CCgirl6690 on 2016-05-05
@Qlll   Thank you. I just didnt know how to describe my problem in one line of title.

---

### Post by izznogooood on 2016-05-05
You dont say what kind of Java you are running so I'm guessing its java from the official repositories. In my experience many (some) java apps don't run properly on anything but Oracle Java (Original java).

The way you can get this in Ubuntu is open a terminal and:

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt update
sudo apt install oracle-java9-installer
```

This will also install the java plug-in for Firefox.

---

### Post by spjackson on 2016-05-05
"Unsupported major.minor version" means that the java version of the runtime is lower than the version used to compile classes, for example if compilation has taken place with Java 8 and you try to run the result on Java 7.

---

### Post by CCgirl6690 on 2016-05-05
Thanks everyone. My java is 7. How can i get 8?

---

### Post by CCgirl6690 on 2016-05-05
> **izznogooood said:**
> You dont say what kind of Java you are running so I'm guessing its java from the official repositories. In my experience many (some) java apps don't run properly on anything but Oracle Java (Original java).

The way you can get this in Ubuntu is open a terminal and:

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt update
sudo apt install oracle-java9-installer
```

This will also install the java plug-in for Firefox.

Hello Sir  
I tried that and i got the followowing errors.... 
Besides i have java 7 now and i want 8 and not 9. 
Can oyu please provide commands for 8 and not 9?  
Thanks ,,,
```
$ sudo add-apt-repository ppa:webupd8team/java
[sudo] password for none: 
 Oracle Java (JDK) Installer (automatically downloads and installs Oracle JDK7 / JDK8 / JDK9). There are no actual Java files in this PPA.

More info (and Ubuntu installation instructions):
- for Oracle Java 7: http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
- for Oracle Java 8: http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html

Debian installation instructions:
- Oracle Java 7: http://www.webupd8.org/2012/06/how-to-install-oracle-java-7-in-debian.html
- Oracle Java 8: http://www.webupd8.org/2014/03/how-to-install-oracle-java-8-in-debian.html

Important!!! For now, you should continue to use Java 8 because Oracle Java 9 is available as an early access release (it should be released in 2016)! You should only use Oracle Java 9 if you explicitly need it, because it may contain bugs and it might not include the latest security patches! Also, some Java options were removed in JDK9, so you may encounter issues with various Java apps. More information and installation instructions (Ubuntu / Linux Mint / Debian): http://www.webupd8.org/2015/02/install-oracle-java-9-in-ubuntu-linux.html
 More info: https://launchpad.net/~webupd8team/+archive/ubuntu/java
Press [ENTER] to continue or ctrl-c to cancel adding it

Error reading https://launchpad.net/api/1.0/~webupd8team/+archive/java: ''
```

---

### Post by QIII on 2016-05-05
See post #4.

However, I would substitute java8 instead of java9, given that the release date for Java 9 is this coming September.

Come to think of it, I think I read somewhere that the Java 9 release has been pushed back to 2017.

---

### Post by CCgirl6690 on 2016-05-05
> **QIII said:**
> See post #4.

However, I would substitute java8 instead of java9, given that the release date for Java 9 is this coming September.

Come to think of it, I think I read somewhere that the Java 9 release has been pushed back to 2017.

How can i choose java 8 in that command? 
Can you please provide commands for it?
Thanks

---

### Post by QIII on 2016-05-05
In the third command, simply replace "java9" with "java8".

---

### Post by izznogooood on 2016-05-05
I see you have a problem with adding the Repository, are you behind a proxy? (can you reroute when you do this?) You just need the key...

---

### Post by CCgirl6690 on 2016-05-05
> **izznogooood said:**
> I see you have a problem with adding the Repository, are you behind a proxy? (can you reroute when you do this?) You just need the key...

thanks it worked and solved my problem,,,,
Can you please take a look at my other thread as well/? 
Thanks

---

### Post by izznogooood on 2016-05-05
That link (in the first post) leeds to this thread... Just edit the link and I can have a look later.

---

