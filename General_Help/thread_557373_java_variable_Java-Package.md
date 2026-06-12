---
title: "java variable Java-Package"
date: 2007-09-22
forum: General Help
---

### Post by ubuntubrian on 2007-09-22
I want to run OpenProj and it requires Java >1.5. I currently get an error:
~/openproj-0.9.4$ ./openproj.sh
Java auto-detection...
Checking java
    Java version: 1.4.2 NOK, version < 1.5
Checking /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java
    Java version: 1.4.2 NOK, version < 1.5
Checking /usr/lib/jvm/java-gcj/bin/java
    Java version: 1.4.2 NOK, version < 1.5
Java not found or incorrect version.
Please install Sun JRE 1.5+ or set JAVA_HOME environment variable if it's already installed.

I run:

 sudo update-alternatives --config java Password:

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/java-j2sdk1.4-ibm
      2        /usr/bin/java-sablevm
      3        /usr/bin/gij-wrapper-4.1
      4        /usr/lib/j2re1.5-ibm/jre/bin/java
      5        /usr/lib/j2sdk1.5-ibm/bin/java
*+    6        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:

If I select any 1.5 option, like 5, I get:
 java -version
JVM not found: libjvm.so  - libjvm.so

So I choose 1 or 6 and I have Java 1.4, too low a version

I added to /etc/bash.bashrc:
JAVA_HOME=/usr/lib/j2re1.5-ibm/jre/bin/java
export JAVA_HOME


 and /etc/environmen by addingt:

JAVA_HOME="/usr/lib/j2re1.5-ibm/jre/bin/java"

 to add the 1.5 version with one of the paths above. Still no good for OpenProj. However when I select #4 above, Thunderbird finds it to run Spamato which requires it but I put that specifically in the Spamato configuration file. I don't know how to do that with OpenProj shell script.

Any ideas on this?

---

### Post by ubuntubrian on 2007-09-22
I tried running with:
/usr/lib/j2sdk1.5-ibm/bin/java -jar openproj.jar

and get an error that only SunJava will work. It seems that OpenProj releases up to 0.9.4 will run on IBM Java. As  I am on PPC I cannot install Sun Java but I can Blackdown, GCJ and IBM. Damn Sun!!
:(

---

### Post by ubuntubrian on 2007-09-22
I found that sablevm will run versions earlier than 0.9.4 also

---

