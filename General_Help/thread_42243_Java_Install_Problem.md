---
title: "Java Install Problem"
date: 2005-06-16
forum: General Help
---

### Post by jakew1991 on 2005-06-16
Hola,

I'm trying to install the Java Runtime; but I can't get it to work.  I've tried using Synaptic, the Ubuntu Guide method (it said the package couldn't be found), and the actual Java web site itself, but it still won't work.  I am trying to determine if it worked or not by typing at the terminal **java -version**.  What should I do??

 - Jake ]

---

### Post by soonindallas on 2005-06-16
I went here: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) and got the java vm and followed the instructions.

IIRC the only tricky part of the install procedure was to place the self-installer in the target directory.  The suggested default usr/java of course does not exist when you set out.

All went well for me.

Now if I type "java -version"

I get:

java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)

---

### Post by jakew1991 on 2005-06-16
[QUOTE=soonindallas]I went here: [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) and got the java vm and followed the instructions.

IIRC the only tricky part of the install procedure was to place the self-installer in the target directory.  The suggested default usr/java of course does not exist when you set out.

All went well for me.

Now if I type "java -version"

I get:

java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)[/QUOTE]
 I got it working now, but thanks for the reply.  I went to:

[http://www.ubuntuforums.org/showthread.php?t=41830&highlight=java](http://www.ubuntuforums.org/showthread.php?t=41830&highlight=java)

 - Jake

---

