---
title: "Oracle JDK manual download"
date: 2013-03-31
forum: General Help
---

### Post by ashishyadav26 on 2013-03-31
Hi,

Is there a manual download site for jdk as is there for jre?

[http://java.com/en/download/linux_manual.jsp](http://java.com/en/download/linux_manual.jsp)


Downloading from [http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html) is difficult as its time out and does not resume. Also its auth. parms gets expired soon, because of which one has to start fresh every time.

---

### Post by mechdave on 2013-04-01
I just use the default-jdk or default-jre (java development kit or java runtime environment) found in the repositories :)

---

### Post by Cheesemill on 2013-04-01
You can use the following commands to install the Oracle Java JDK...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by slickymaster on 2013-04-01
Until the beginning of last year you could do it by terminal, just running the command wget, but now if you try to do
```
wget http://download.oracle.com/otn-pub/java/jdk/7u17-b02/jdk-7u17-linux-i586.tar.gz
```
you end up with a small HTML file that states:
"In order to download products from Oracle Technology Network you must agree to the OTN license terms."
and
"Be sure that...
Your browser has "cookies" and JavaScript enabled.
You clicked on "Accept License" for the product you wish to download.
You attempt the download within 30 minutes of accepting the license."

Oracle changed their licensing last year to preclude Linux distributions from packaging Oracle's JDK.

---

