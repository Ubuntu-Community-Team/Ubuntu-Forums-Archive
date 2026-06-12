---
title: "Limewire not detecting java"
date: 2006-12-27
forum: General Help
---

### Post by HwH on 2006-12-27
for some reason limewire is not detecting my java plugin i have tried installing it 3 ways now and it detects none of them

```
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
```

any help would be good

thank you in advance

---

### Post by Cows on 2006-12-27
Yea that was happening to me when i was installing Frostwire ( better but the same =] ). Anyways yea you will just need to go to your Add/Remove applications and search for java, Then install the java runtime environment 5.0 and the java plugin. Click ok and there you go.

---

### Post by ashmew2 on 2007-01-25
If your limewire isnt detecting Java , first of all make sure u have it installed :
1) Enable Multiverse and Universe Repositories.
2) In a terminal type :
sudo apt-get install sun-java5-jre sun-java5-plugin 
3)After java is finished installing , u need to configure Java , do this in terminal : 
sudo update-alternatives --config java
4)Make a selection , which i think must be /usr/lib/jvm/java-gcj/jre/bin/java although im not very sure.
5)Start Limewire and post ur feedback!!
Hope this helped :)

---

### Post by Iarwain ben-adar on 2007-02-03
ashmew2:

Thanks!


Iarwain

---

