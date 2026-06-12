---
title: "[SOLVED] unable to update security issues"
date: 2007-12-19
forum: General Help
---

### Post by Bobrm2 on 2007-12-19
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Bobrm2 on 2007-12-19
When I 

sudo dpkg --configure -a' 

I get:

bob@Bob:~$ sudo dpkg --configure -a
[sudo] password for bob:
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

I have downloaded both jdk-6-doc.zip and jdk-6-doc.ja.zip and the are in /tmp and /usr/java


I have been attempting to repair my java files, having four different instances: believing that I have two different java attempting to connect to my banking site at the same time (neither is able to do so).  I don not know if I have two different problems or the confused java issue is the cause for both problems



Could someone tell me how to correct these or this problem. Thank you

---

### Post by Bobrm2 on 2007-12-22
as noted above and when running dpkg --configure -a in the terminal I am asked to provide (download) a java document installing it in /tmp etc. 

Searching my files I have the file(s); but I had no files in /usr/java. So, and according with instruction from the Java site, I have download most recent java file placing them in /usr/java and linking the file to mozilla/plugin.

Then I went to /usr/lib/jvm and deleted the contents of the /jvm folder.

Trying to install the security updates, results in the same problem(s). i.e.
bob@Bob:~$ sudo dpkg --configure -a
[sudo] password for bob:
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


Since I have completely install the most recent addition of Java to /usr/java why do I need to download the jdk-6-doc.zip and unzip it in the /tmp. I have agreed to the document when installing in /usr/java.

This bug is noted, I have no idea where to submit a further bug report or how to locate a solution, other than the search efforts (google and gutsy) I have already done, will continue in that vein.

Any help appreciated.

Bob

---

