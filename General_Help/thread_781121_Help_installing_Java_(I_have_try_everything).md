---
title: "Help installing Java (I have try everything)"
date: 2008-05-04
forum: General Help
---

### Post by braveerudite on 2008-05-04
I have Ubuntu 8.04 x64 Edition.  I can't get Java to pass [this]("http://www.java.com/en/download/help/testvm.xml") test.

There are so many versions of Java that it gets really confusing.  Would someone please help getting Java to work properly in my new Ubuntu install.


Thank you all for your time.

---

### Post by gsiliceo on 2008-05-04
I have the sun java highest version available in the repositories and i can run frostwire wich uses java and a few other apps in java but cant pass that test. I wouldnt mind because its been literally years since i ran into a webpage that needed java.
Mind you, dont confuse java with javascript.

---

### Post by braveerudite on 2008-05-04
> **gsiliceo said:**
> I have the sun java highest version available in the repositories and i can run frostwire wich uses java and a few other apps in java but cant pass that test. I wouldnt mind because its been literally years since i ran into a webpage that needed java.
Mind you, dont confuse java with javascript.

Thank you for your reply.

The problem is that I need Java in order to connect remotely to my home server using [www.logmein.com](www.logmein.com).  The way is done (I can see the computer I'm controlling) is threw my browser and Java.

---

### Post by gsiliceo on 2008-05-04
Oh, im sorry i don't know anything about it.

---

### Post by jamesstansell on 2008-05-04
Sun doesn't ship a 64bit browser plugin yet.  I think their plan is to release one next year.  The icedtea-gcjwebplugin package may be worth trying, but I don't run 64bit so I don't have any actual experience.  At least it has a 64bit version:

[https://launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/1.0-0ubuntu5](https://launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/1.0-0ubuntu5)

Check the 64-bit users forum - they have a sticky thread about Java.

---

### Post by frenchn00b on 2008-05-04
> **braveerudite said:**
> I have Ubuntu 8.04 x64 Edition.  I can't get Java to pass [this]("http://www.java.com/en/download/help/testvm.xml") test.

There are so many versions of Java that it gets really confusing.  Would someone please help getting Java to work properly in my new Ubuntu install.


Thank you all for your time.
 
try first with iceape & 
and```
 apt-get install sun-java6-bin
```
java -version ?
1.6?

or:
if not: ```
ln -s /usr/lib/... jvm/java1.6sun stuff/ java       /usr/bin/java16 
``` to adapt
  
and try with iceape & again

---

### Post by Tibor60 on 2008-05-04
It will be a hard job. I was struggling with  it for  acouple of days, no success, so I reinstalled the Heron 32 bit version. And eve here the buil-in java was not functioning. I had to reinstall all the java stuff and icedtea-wcjwebplugin, even the firefox, all with the --purge option, and then reinstalled first firefox-3.0, then the java version from sun:
sun-java6-bin sun-java6-jre sun-java6-plugin. And then all were going normally. It seems that only the sun version is good for firefox-3, but sun has no 64 bit version.

---

