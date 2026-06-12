---
title: "Javac/Java Not Working - but Installed?"
date: 2008-01-03
forum: General Help
---

### Post by Syndacate on 2008-01-03
Alright, I got this isssue here with Java...

See, it's a pain in the *** to upload something to the server then SSH using a different konsole in to compile it and run it - and I don't feel like using eclipse for smaller projects.

So I tried "javac" in Konsole, it said it's not available, but it's availbale in the following packages *lists packages* - So I select one that seems about right (java 6) - I use javac, it compiles fine.

I go to type Java ProgramName though - and get the following error:
```

Exception in thread "main" java.lang.UnsupportedClassVersionError: StringThing (Unsupported major.minor version 50.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

```

Blah blah blah - java works right on my computer (I can go to a website and view Java), but it's not working there, anybody any ideas?

EDIT:
PS:  It's not a compilation error because it compiles fine if I FTP it to my school's server, and compile it then run it remotely.

---

### Post by taurus on 2008-01-03
What version do you have installed on your machine?  What's the output of this command from a terminal?

```
java -version
```

---

### Post by Syndacate on 2008-01-04
> **taurus said:**
> What version do you have installed on your machine?  What's the output of this command from a terminal?

```
java -version
```

```

java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

I used aept installer to dl/install Java 5 though :\

---

### Post by Sef on 2008-01-04
> I used aept installer to dl/install Java 5 though :\

> java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

It says you have downloaded blackdown, which is version 1.4.   Did you also download 1.5?

---

### Post by jespdj on 2008-01-04
First, make sure that you have installed Sun Java 6:
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```
(Note, this will install the JDK, which includes the Java compiler).

Then, make sure that Sun Java 6 is the default Java that's being used on your system:
```
sudo update-alternatives --config java
```
Select Sun Java 6 in the menu that the last command shows.

The error message you get means that you are trying to running a Java program that was compiled with a newer version of Java on an older version of the JVM.

---

### Post by Syndacate on 2008-01-04
> **jespdj said:**
> First, make sure that you have installed Sun Java 6:
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
```
(Note, this will install the JDK, which includes the Java compiler).

Then, make sure that Sun Java 6 is the default Java that's being used on your system:
```
sudo update-alternatives --config java
```
Select Sun Java 6 in the menu that the last command shows.

The error message you get means that you are trying to running a Java program that was compiled with a newer version of Java on an older version of the JVM.

Worked - thanks - Yeah, I didn't think I was that stupid, I knew I installed Java :P.

the install of sun-java6 and the plugin did nothing (nothing updated, nothing installed, everything already there), but it wasn't set as default, set it as default, worked like a charm.

Thanks a bunch man.

---

