---
title: "Need help running elcipse on ubuntu"
date: 2013-02-18
forum: General Help
---

### Post by symaticc on 2013-02-18
I downloaded eclipse and the java developement kit and they are in the same folder, the JDK is in the eclipse.exe folder and when I try to run eclipse, it gives me this error
"A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/username/Code/eclipse/jre/bin/java
java in your current PATH"

I tried searching for that path and when I go to Code/eclipse, there is no jre file so I dont even know where it is searching. Can anyone help me out?

Thanks in advance!

---

### Post by symaticc on 2013-02-23
Okay so I retried and first download Eclipse classic 64bit for linux from here:
[http://www.eclipse.org/downloads/packages/eclipse-classic-421/junosr1](http://www.eclipse.org/downloads/packages/eclipse-classic-421/junosr1)

and then I downloaded JDK 7u15 for the linux .tar.gz file from here:
[http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)

but it is stil giivng me the same error. I dont have the JDK inside the eclipse folder either. I created a folder called code and put both the JDK and eclipse folder in it and then I opened the eclipse folder and ran the eclipse.exe file but it still gives me the same error. Any ideas on how to fix this? thanks in advance!

---

### Post by r-senior on 2013-02-23
Did you try installing Eclipse and OpenJDK from the repositories, e.g. by using Software Centre?

---

### Post by symaticc on 2013-02-23
> **r-senior said:**
> Did you try installing Eclipse and OpenJDK from the repositories, e.g. by using Software Centre?

Hm, the eclipse which is on the sofware centre, is it the same as the eclipse classic which I downloaded from the website? Also, when I run the eclipse which I downlaoded from the software centre, it says that it is version 3.8, how do I get the latest eclipse 4.2.1 version?

---

### Post by Gyokuro on 2013-02-23
> **symaticc said:**
> Okay so I retried and first download Eclipse classic 64bit for linux from here:
[http://www.eclipse.org/downloads/packages/eclipse-classic-421/junosr1](http://www.eclipse.org/downloads/packages/eclipse-classic-421/junosr1)

and then I downloaded JDK 7u15 for the linux .tar.gz file from here:
[http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)

but it is stil giivng me the same error. I dont have the JDK inside the eclipse folder either. I created a folder called code and put both the JDK and eclipse folder in it and then I opened the eclipse folder and ran the eclipse.exe file but it still gives me the same error. Any ideas on how to fix this? thanks in advance!

It means that eclipse can not find your downloaded JDK. You should extract JDK 7u15 to /opt/ 

and afterwards you should have /opt/jdkXXXX (XXXx is for your downloaded jdk release)

now you should inform your system that you want to use a different JDK:

sudo update-alternatives --install "/usr/bin/java" "java" "/opt/jdkXXXX/bin/java" 1 
sudo update-alternatives --install "/usr/bin/javac" "javac" "/opt/jdkXXXX/bin/javac" 1

and now you can choose your default java via:

sudo update-alternatives --config java

and enter the number which belongs to your JDK in /opt/ and Eclipse should be happy.

---

