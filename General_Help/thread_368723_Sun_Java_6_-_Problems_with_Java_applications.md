---
title: "Sun Java 6 - Problems with Java applications"
date: 2007-02-23
forum: General Help
---

### Post by core on 2007-02-23
Hi all,

I'll try to make this short. I just installed Eclipse from Edgy repositories but I wanted it to use Sun's Java SDK. So I downloaded and installed Java 6 SDK from the same repositories. And now I messed up: I didn't want Gnu Java Compiler at the same time so *i think* I removed it. From this point on, Eclipse didn't start, not even after a complete removal and reinstallation of the package. The error message remains:

```
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java
```

Azureus works with Java 6 but crashes with 'core dumped'.

I been around removing and reinstalled packages but no success.. does anyone knows how to get around this issue?

Thanks in advance.

---

### Post by flossgeek on 2007-02-23
To set the sun java machine you should do this(taken from ubuntu wiki):-

> "If you want to use Sun's Java instead of the open source GIJ (GNU Java bytecode interpreter) you need to set it as default. To list installed JVMs:

  update-java-alternatives -l

To select, for example, Sun's JVM as provided in Ubuntu 6.06, run:

  sudo update-java-alternatives -s java-1.5.0-sun

You should also edit /etc/jvm and move /usr/lib/jvm/java-1.5.0-sun to the top of JVMs offered."

Also there is no need to install Eclipse via apt-get, you can get the latest download from site and it will runn as long as your java environment is functioning. 

See:- [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)> 

---

### Post by core on 2007-02-23
I managed to get around it, inserting the Java 6 JVM root dir at /etc/eclipse/java_home. But Azureus is still crashing :/

Any ideas on this? Sorry for the inconvenience.

---

### Post by flossgeek on 2007-02-23
Good, but I know nothing about Azureus, I haven't used it, so I can't really advise. Have you tried running it on the 1.5 version of Java.

---

### Post by phossal on 2007-02-23
Core, what version of Ubuntu are you running?

---

### Post by core on 2007-02-24
I'm using Edgy,

I've managed to work around this after understanding where JVM's are found. I Also managed to install Gnu Java Compiler properly again and now Azureus uses it and doesn't crash.

Also Eclipse is working like a charm.

Thanks for you support..

---

### Post by phossal on 2007-02-24
> **core said:**
> I've managed to work around this after understanding where JVM's are found. 
Careful, though, because they're *not* always found there, and eclipse *doesn't* always seek *javac*, the compiler, the same way. It depends on whether you're using packages or not.

Glad you're up and running - just something to keep in mind if you decide to do things differently in the future.

---

