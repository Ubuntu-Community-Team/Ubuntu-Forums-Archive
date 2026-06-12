---
title: "maple 11 install error"
date: 2007-05-05
forum: General Help
---

### Post by sonium on 2007-05-05
Hi, maple11 is not installable. I already tried installing sun-java6

The error is:
```

sonium@sonium-laptop:~/Desktop$ ./Maple11Linux32Installer.bin -helpPreparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2481: /tmp/install.dir.9513/Linux/resource/jre/bin/java: not found
```

---

### Post by taurus on 2007-05-05
What's the output of this command from a terminal?

```
java -version
```

---

### Post by sonium on 2007-05-05
```
sonium@sonium-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)

```

I forgot to mention the file in the last line actually exists.

---

### Post by durus on 2007-10-20
Did you manage to install Maple 11 ? I have the same problem.

---

### Post by durus on 2007-10-20
Sorry, wrong topic and I cant remove this post

---

### Post by sonium on 2007-10-21
> **durus said:**
> Did you manage to install Maple 11 ? I have the same problem.

Yes, there is a command line switch where you can specify tha you're gonna use the 32bit version.
atm I don't have installed it an I can't remeber what option it was.

---

