---
title: "Running JARs on Ubuntu"
date: 2013-01-16
forum: General Help
---

### Post by mindinsomnia on 2013-01-16
I've just spent about 6 hours googling this, I'm angry, I'm frustrated, I really need help, I really need some simple answers and I don't know where else to go now.

This is the problem:

I have a stand alone java application, a jar. It's a simple application with a GUI. On Windows, this runs perfectly fine by double clicking the file. The application starts, the GUI shows. I had to do nothing special to make this work, other than installing the JRE on Windows, which can be downloaded from the website and installs in about 5 minutes with minimal user interaction.

I want to do the exact same thing on Ubuntu.

So I have my jar file which works perfectly fine on Windows. I double click the file, it opens in an archive manager. I go to Open With and pick the Open JDK and it tells me it's not executable. I change the permissions in the properties and now it does nothing when I run it. I run it with Open JDK Runtime 6/7, nothing happens. I try running it from terminal with java -jar /path/to/file/Example.jar. I get an error saying the main class file was not found.

I need to know how to run JARs on Linux, and more specifically, I need to know how to do so in a way which average computer illiterate people can understand as well.

I learnt Java (and in the process of learning JOGL) so that I could create applications and release them crossplatform across Windows/Mac/Linux, because I want to support all OSes equally. But so far from what I've experienced, I wouldn't expect any normal computer user to be able to figure out how to even run Java applications, which makes what I'm doing feel kinda pointless.

So is there something I'm missing?

Is there some kind of easy to use double click installer which can fix  up and install Java on Ubuntu  to make this work like in Windows? Is there  some kind of 'just run it' script I can write which will make a JAR run perfectly  with no problem? Is there some kind of packager for JARs on Linux which  will check for the JRE and install it automatically for Linux?

There has to be SOMEWAY of getting this to work so that a user can just double click a file and it'll run the application. Surely there has to be a way! I can't figure it out though and it's driving me bonkers. This took like 5 minutes in Windows and it's already taken me 5 hours in Ubuntu still with no solution. What am I missing?

---

### Post by c2tarun on 2013-01-16
> **mindinsomnia said:**
> I've just spent about 6 hours googling this, I'm angry, I'm frustrated, I really need help, I really need some simple answers and I don't know where else to go now.

This is the problem:

I have a stand alone java application, a jar. It's a simple application with a GUI. On Windows, this runs perfectly fine by double clicking the file. The application starts, the GUI shows. I had to do nothing special to make this work, other than installing the JRE on Windows, which can be downloaded from the website and installs in about 5 minutes with minimal user interaction.

I want to do the exact same thing on Ubuntu.

So I have my jar file which works perfectly fine on Windows. I double click the file, it opens in an archive manager. I go to Open With and pick the Open JDK and it tells me it's not executable. I change the permissions in the properties and now it does nothing when I run it. I run it with Open JDK Runtime 6/7, nothing happens. I try running it from terminal with java -jar /path/to/file/Example.jar. I get an error saying the main class file was not found.

I need to know how to run JARs on Linux, and more specifically, I need to know how to do so in a way which average computer illiterate people can understand as well.

I learnt Java (and in the process of learning JOGL) so that I could create applications and release them crossplatform across Windows/Mac/Linux, because I want to support all OSes equally. But so far from what I've experienced, I wouldn't expect any normal computer user to be able to figure out how to even run Java applications, which makes what I'm doing feel kinda pointless.

So is there something I'm missing?

Is there some kind of easy to use double click installer which can fix  up and install Java on Ubuntu  to make this work like in Windows? Is there  some kind of 'just run it' script I can write which will make a JAR run perfectly  with no problem? Is there some kind of packager for JARs on Linux which  will check for the JRE and install it automatically for Linux?

There has to be SOMEWAY of getting this to work so that a user can just double click a file and it'll run the application. Surely there has to be a way! I can't figure it out though and it's driving me bonkers. This took like 5 minutes in Windows and it's already taken me 5 hours in Ubuntu still with no solution. What am I missing?

Hi mindinsomnia, be calm someone will surely help you here. Meanwhile I want you to share two information with us.

1. What was the compiler you used on windows? Was it the same as openjdk?
2. What is happening when you are trying to run it on linux? Pleas share the output you get when you try to run it on Linux

---

### Post by mindinsomnia on 2013-01-17
I used Eclipse and the JDK, JavaSE-1.7. When I open the JAR in Ubuntu, it comes up with:

Blocked: /user/bin/java -jar
The file /home/grady/Dropbox/Java/GraphicalUI/bin/StartHere.jar' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit.

So I go into properties and make it as executable and try again. I'm opening it with OpenJDK Java 7 Runtime, I also have OpenJDK Java 6 Runtime installed though on Ubuntu.

When I try running the JAR from command line using the usual method:
java -jar /home/grady/Dropbox/Java/GraphicalUI/bin/StartHere.jar
I get this output:
Exception in thread "main" java.lang.UnsupportedClassVersionError: StartHere : Unsupported major.minor version 51.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: StartHere. Program will exit.

Yet the exact same JAR on Windows 7 64bit, it runs just fine with no problems at all, I can just double click it and it runs instantly. The application is just simply a test I'm using to test running Java applications on Ubuntu, it uses no external libraries and only what's in JRE System Library, mostly just a bunch of Swing components. It couldn't be anymore basic.

---

### Post by c2tarun on 2013-01-17
> **mindinsomnia said:**
> I used Eclipse and the JDK, JavaSE-1.7. When I open the JAR in Ubuntu, it comes up with:

Blocked: /user/bin/java -jar
The file /home/grady/Dropbox/Java/GraphicalUI/bin/StartHere.jar' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit.

So I go into properties and make it as executable and try again. I'm opening it with OpenJDK Java 7 Runtime, I also have OpenJDK Java 6 Runtime installed though on Ubuntu.

When I try running the JAR from command line using the usual method:
java -jar /home/grady/Dropbox/Java/GraphicalUI/bin/StartHere.jar
I get this output:
Exception in thread "main" java.lang.UnsupportedClassVersionError: StartHere : Unsupported major.minor version 51.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: StartHere. Program will exit.

Yet the exact same JAR on Windows 7 64bit, it runs just fine with no problems at all, I can just double click it and it runs instantly. The application is just simply a test I'm using to test running Java applications on Ubuntu, it uses no external libraries and only what's in JRE System Library, mostly just a bunch of Swing components. It couldn't be anymore basic.


Well I cannot promise that this will work, but try installing Oracle Java 7 SE.
For help visit this link: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

dont forget to check which version of java is in operation now, you can check that by running: 

```
java -version 
```

in terminal.

---

### Post by veroslav on 2013-01-17
You usually get that kind of exception if you compile with a JDK version that is higher than the one you are using when running the jar.

---

### Post by mindinsomnia on 2013-01-17
SUCCESS!

Spot on about the version number problem. I saw JRE 7 installed and just figured Ubuntu would use it. It also had JRE 6 installed though and was using it by default. I found this:

[http://blog.rajatpandit.com/2010/04/17/changing-default-jre-for-ubuntu-installations/](http://blog.rajatpandit.com/2010/04/17/changing-default-jre-for-ubuntu-installations/)

And using those commands was able to figure out how to set the JRE 7 as the default, now the JARs run as they do and the application loads just fine! Even my JOGL application runs perfectly well, 3 cheers for working cross platform hardware accelerated 3D graphics!

Thanks for the help, I greatly appreciate it.

---

### Post by veroslav on 2013-01-17
You are welcome, glad you got it fixed :)

---

