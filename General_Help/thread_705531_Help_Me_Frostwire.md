---
title: "Help Me Frostwire"
date: 2008-02-23
forum: General Help
---

### Post by skylinedna on 2008-02-23
I downloaded all java plugins i could and went to run frostwire but came back with 

Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

i gather i have a version thats old but how do i dontload the newer one and will that solve the problems cause there looks to be more wrong than just having the older version

thanks

---

### Post by santiagoward2000 on 2008-02-23
Hi!
Are you on Gusty? If so, all you need to do is open Add/Remove... and install **Sun Java 6 Console** and **Sun Java Web Start**.
Good luck!

---

### Post by taurus on 2008-02-23
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```
Make sure it says version 1.6 from the last output.

Otherwise, reconfigure it again after you've installed Sun java 1.6.

```
sudo update-alternatives --config java
```

---

### Post by skylinedna on 2008-02-23
thanks that worked fine. now only to get it to connect..

---

### Post by santiagoward2000 on 2008-02-23
> **skylinedna said:**
> thanks that worked fine. now only to get it to connect..

Do you have problems connecting FrostWire? Perhaps you are behind a firewall and need to configure it.

---

### Post by skylinedna on 2008-02-23
nope i not behind firewall. and ive been through that copy and paste gnutella stuff... but my connection is weak atm mayb that could hinder it

---

### Post by seventhc on 2008-02-23
I had this happen on mine, all I did was disconnect and reconnect from the file menu. 
For me, that gets it connected. Not sure if it will work for you or not, but worth a try.

---

