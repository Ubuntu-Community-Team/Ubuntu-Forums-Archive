---
title: "java runtime errors - *not* due to program"
date: 2008-05-15
forum: General Help
---

### Post by Xiong Chiamiov on 2008-05-15
So, the only reason I've got java installed on my system at all is for class, which makes it rather necessary.  I hadn't run anything for a little while, and I use my system pretty heavily, so I have no idea what it is that I did to break things.
Here's the short of it: when I try to run things that require imports, they compile just fine, but don't run, with a message like this:
```

Exception in thread "main" java.lang.NoClassDefFoundError: java.util.Scanner                                             at HashTest.main(HashTest.java:5)

```
I know that my programs are alright because a) I'm importing things correctly and b) they run just fine on my school account (when I transfer files and ssh in).

It seems that it has something to do with the classpath, but I've tried both running with the -classpath . option and adding 
```

export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin

```
to the end of my ~/.bashrc file.

Another interesting bit is that, even though I have java 6 installed (and not 5), java -version returns
```

java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by Mr A Mouse on 2008-05-15
It looks very much like you have two versions of java installed, and the computer is looking to Java 1.5. Have you checked Synaptic to make sure of the status on 1.5?

---

### Post by Xiong Chiamiov on 2008-05-15
I'm actually using adept, but here's the result of
```

aptitude search '~i' | grep java

```:
```

i A java-common                     - Base of all Java packages                 
i A java-gcj-compat                 - Java runtime environment using GIJ        
i A java-gcj-compat-headless        - Java runtime environment using GIJ (headle
i A libbcel-java                    - Analyze, create, and manipulate (binary) J
i   libecj-java                     - Eclipse Java compiler (library)           
i   libecj-java-gcj                 - Eclipse Java compiler (native library)    
i   libjaxp1.3-java                 - Java XML parser and transformer APIs (DOM,
i   libjline-java                   - Java library for handling console input   
i A liblog4j1.2-java                - Logging library for java                  
i A libmx4j-java                    - An open source implementation of the JMX(T
i A libregexp-java                  - regular expression library for Java       
i A libswt3.2-gtk-java              - Fast and rich GUI toolkit for Java, gtk2 v
i   libxalan2-java                  - XSL Transformations (XSLT) processor in Ja
i   libxerces2-java                 - Validating XML parser for Java with DOM le
i   openoffice.org-java-common      - OpenOffice.org office suite Java support a
i A sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
i A sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (

```

This only lists those that have java in the name, not the description, though, so it doesn't include bsh, gij, junit4, and a few others.  I can type them out if it'll help.

---

### Post by Mr A Mouse on 2008-05-15
It looks like you have GCJ Java and Sun Java both installed. I would remove one or the other of them.

---

### Post by Xiong Chiamiov on 2008-05-15
Ah, that fixed the problem.  I was sure it was something stupid, but I wasn't quite sure, with the abundance of java packages and whatnot.

---

### Post by Mr A Mouse on 2008-05-15
Ah, but that's not "something stupid"--that's one more step on the learning curve. :)

---

### Post by Xiong Chiamiov on 2008-05-15
> **Mr A Mouse said:**
> Ah, but that's not "something stupid"--that's one more step on the learning curve. :)
Ah, yes, learning, bit by bit, day by day.

---

### Post by jamesstansell on 2008-05-19
> **Xiong Chiamiov said:**
> Ah, yes, learning, bit by bit, day by day.

Learn a little more, and you'll know how to successfully have all 6 versions of Java installed at the same time!

---

