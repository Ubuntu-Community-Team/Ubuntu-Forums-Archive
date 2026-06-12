---
title: "Trouble updating Java"
date: 2015-07-17
forum: General Help
---

### Post by SuperFreak on 2015-07-17
Noticed that Firefox 39 indicates my Java plugin is out of date. Followed [THESE]("http://www.java.com/en/download/help/linux_x64_install.xml") instructions and downloaded Linux X64 tar.gz file and installed. Plugin still doesn't register as updated

---

### Post by claracc on 2015-07-18
You can try an straightforward way of installing java through the webup8 ppa: [https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)

---

### Post by SuperFreak on 2015-07-18
Thanks I tried this and I am getting errors

```
david@MainSqueeze:~$ su -
Password: 
su: Authentication failure
david@MainSqueeze:~$ sudo echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee /etc/apt/sources.list.d/webupd8team-java.list
tee: /etc/apt/sources.list.d/webupd8team-java.list: Permission denied
[sudo] password for david: 
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
david@MainSqueeze:~$ sudo echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee -a /etc/apt/sources.list.d/webupd8team-java.list
tee: /etc/apt/sources.list.d/webupd8team-java.list: Permission denied
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
david@MainSqueeze:~$ 

```

Found further directions[ HERE]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") for Ubuntu . Followed instructions but says that Java is already installed but Firefox says it needs updating

---

### Post by claracc on 2015-07-19
Well, I have a similar situation in my ubuntu 14.04 fallback fully updated.

Java plugins in firefox: see attached window, 10.60.2 and 10.80.2 and any case java web page says I have an outdated java.

If I run in terminal java -version, this is what I have:

clara@clara1:~$ java -version
java version "1.7.0_80"
Java(TM) SE Runtime Environment (build 1.7.0_80-b15)
Java HotSpot(TM) Server VM (build 24.80-b11, mixed mode)

I use the webup8 ppa for updating oracle java, and I have the last oracle java 7 plugin, there is not any one newer. But java and firefox say the plugin is outdated.

is there any security problem with last oracle java 7 plugin ?, Is advisable to install the java 8?, what is the problem ?

---

### Post by claracc on 2015-07-19
I attach the java plugins informationfrom add-ons tab in forefox, since I forgot to attach in previous comment

---

### Post by gnwiii on 2015-07-19
The webupd8team PPA hasn't been updated to the current Oracle versions, so if you need Java in a browser you will have to download the Oracle JDK in .tar.gz format and install manually.  This has been discussed in another thread where I posted an outline of the steps needed for a manual install.

---

