---
title: "Java based programs not installing"
date: 2018-09-13
forum: General Help
---

### Post by tarakaramji on 2018-09-13
I am trying to install general tools like Cytoscape and Blast2GO by their .sh script and it starts like this 
 Unpacking JRE ...Preparing JRE ...
Starting Installer ...
 and nothing is displayed after that. 
JRE and JDK is installed and in the path 
java 10.0.2 2018-07-17
Java(TM) SE Runtime Environment 18.3 (build 10.0.2+13)
Java HotSpot(TM) 64-Bit Server VM 18.3 (build 10.0.2+13, mixed mode)

Any help and suggestion will be highly appreciated as i could not really find a solution in any of the forums



Thanks in advance

---

### Post by ajgreeny on 2018-09-13
See if the link in my post at [https://ubuntuforums.org/showthread.php?t=2400577&p=13798882&viewfull=1#post13798882](https://ubuntuforums.org/showthread.php?t=2400577&p=13798882&viewfull=1#post13798882) is of any help.

If your program requires java to run to install it this may be the problem and that workaround may solve it for you.

---

### Post by Holger_Gehrke on 2018-09-13
From the Cytoscape [Download page]("http://cytoscape.org/download.php"):> 
**Please install [ Java 8]("http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html") before using Cytoscape**
                 **Java 9 **[sic]** is not yet supported**

So I installed openjdk-8-jdk (not the Oracle Java they link to, I have a slight antipathy towards Oracle and don't use their Software unless nothing else will work ...) and made it the default Java by running:
```

sudo apt install openjdk-8-jdk
sudo update-java-alternatives -s java-1.8.0-openjdk-amd64

```
and both the installer and Cytoscape seem to run (although it does put up a few messages about not having the logger it wants available and OpenCL being either not available or not having the Java-classes to use it). If you need to switch back to Java 10 you can get the list of installed Java JREs and JDKs with 'update-java-alternatives -l' and then run 'sudo update-java-alternatives -s' followed by one of the names listed in the first column of the list. Using the same Java 8 Blast2go installed and ran just as easily. Can't say whether or not both programs are running as they should - I am not a molecular biologist after all - but they do run. 

Holger

---

