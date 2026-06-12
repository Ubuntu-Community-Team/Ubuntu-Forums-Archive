---
title: "Java Problems"
date: 2007-12-07
forum: General Help
---

### Post by Aifel on 2007-12-07
So, I'm trying to install frostwire. It installs fine, but when run, it gives the following output:
ambrose@home-desktop:~$ frostwire 
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ambrose@home-desktop:~$ 

This is on 7.10, BTW. And yes, sun-java5-jre is installed, as well as the bin package.

---

### Post by erfahren on 2007-12-07
[http://ubuntuforums.org/showthread.php?t=633356](http://ubuntuforums.org/showthread.php?t=633356)

---

### Post by taurus on 2007-12-07
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by Aifel on 2007-12-07
> **erfahren said:**
> [http://ubuntuforums.org/showthread.php?t=633356](http://ubuntuforums.org/showthread.php?t=633356)

Yeah, I've read that. I've (re)installed java a bunch of times to no avail. And the directories frostwire is looking for aren't created when I install java...

---

### Post by Aifel on 2007-12-07
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```
That also didn't work.

---

### Post by taurus on 2007-12-07
What's the output of the last command from above?

```
java -version
```

Are you running x86 or x86_64?

---

### Post by Aifel on 2007-12-07
> **taurus said:**
> What's the output of the last command from above?

```
java -version
```

Are you running x86 or x86_64 and which release are you using?

ambrose@home-desktop:~$ java --version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
ambrose@home-desktop:~$ 
 And as said earlier, I'm using 7.10 x86

---

### Post by taurus on 2007-12-07
What's the output of this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by Aifel on 2007-12-07
> **taurus said:**
> What's the output of this command from a terminal?

```
sudo update-alternatives --config java
```

```
sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
*+        3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 
```
Which one do I want?

---

### Post by taurus on 2007-12-07
You want number 4, not 3, as your default java.

---

### Post by Aifel on 2007-12-07
> **taurus said:**
> You want number 4, not 3, as your default java.

Sweet it works. Thanks a bunch.

---

### Post by erfahren on 2007-12-07
> **Aifel said:**
> Sweet it works. Thanks a bunch.
good to hear!

note: you can mark this thread as "Solved" by going to the "Thread Tools" above the first post.

---

