---
title: "[ubuntu studio] openoffice: no java runtime environment"
date: 2007-11-30
forum: General Help
---

### Post by liniaal on 2007-11-30
hi people,

recently installed ubuntu studio 7.10. now i can not seem to get OOo to work :(. if i type oowriter in a terminal, i get the following error lines

```

javaldx: Could not find a Java Runtime Environment! 

** (process:7484): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

i already installed the following packages:
sun-java5-bin
sun-java5-jre
sun-java6-bin
sun-java6-jdk
sun-java6-jre

what could be wrong??

---

### Post by scottfinman on 2008-01-23
Did you find a solution to this problem? I'm running into exactly the same.

---

### Post by Hagar Delest on 2008-01-26
Go to the Tools>Options>OOo>Java panel, make sure there is a java version checked. Wait a while so that OOo scans your HD.

---

### Post by hermelinen on 2008-04-10
> **Hagar de l'Est said:**
> Go to the Tools>Options>OOo>Java panel, make sure there is a java version checked. Wait a while so that OOo scans your HD.

This actually does not work for me. I left it there for more than 10 minutes and nothing happens. I have java 6 from sun installed. Any more ideas? 

Specs:

Ubuntu 7.10 Gutsy
sun-java6-jdk
sun-java6-jre

---

### Post by gaussian on 2008-04-10
> **hermelinen said:**
> This actually does not work for me. I left it there for more than 10 minutes and nothing happens. I have java 6 from sun installed. Any more ideas? 

Specs:

Ubuntu 7.10 Gutsy
sun-java6-jdk
sun-java6-jre

I am not on an Ubuntu machine right now, so I cannot check on the path name. But try the following: 

remove the file ~/.ooo-2.0/user/config/javasettings_Linux_x86.xml

(I am not sure about the .ooo-2.0 part, it could be called something else in Ubuntu).

Restart Openoffice and try selecting java

[I]Edit: The correct path under ubuntu is  ~/.openoffice.org2/user/config
[/I]

---

### Post by webbsd on 2008-05-21
This didn't work for me. I tried removing then entire ~/.openoffice.org2 directory but I still get javaldx: Could not find a Java Runtime Environment!

---

### Post by webbsd on 2008-05-21
I tried installing the openoffice.org metapackage. Unfortunately ooffice now fails to start without giving any error messages.

---

### Post by purachochada on 2008-06-09
found this page: [http://plagatux.es/?p=296]("http://plagatux.es/?p=296") (sorry it's in spanish!)
or this bug report: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139")

in a nutshell...to solve the problem, install **openoffice.org-java-common**

hope that helps

---

### Post by iqson716 on 2008-06-17
hey 
Install openoffice.org database :)

---

### Post by jackn on 2008-06-19
> **purachochada said:**
> found this page: [http://plagatux.es/?p=296]("http://plagatux.es/?p=296") (sorry it's in spanish!)
or this bug report: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139")

in a nutshell...to solve the problem, install **openoffice.org-java-common**

hope that helps

Had same issue as liniaal.
purachochada's solution worked for me.

See [Kunthar's remark]("http://code.google.com/p/openmeetings/wiki/OpenOfficeConverter") to Debian Etch users.

---

### Post by prince_niceguy on 2008-06-19
> **purachochada said:**
> found this page: [http://plagatux.es/?p=296]("http://plagatux.es/?p=296") (sorry it's in spanish!)
or this bug report: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139")

in a nutshell...to solve the problem, install **openoffice.org-java-common**

hope that helps

that worked for me too. thanks.

---

