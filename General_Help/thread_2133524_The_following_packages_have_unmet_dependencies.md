---
title: "The following packages have unmet dependencies"
date: 2013-04-08
forum: General Help
---

### Post by Ali paco on 2013-04-08
Hello guys
I have a problem in one of my packages, when i want to repair it in ubuntu software centre it shows: 

installArchives() failed: (Reading database ... 
dpkg: warning: files list file for package 'pri.ter-driver-pnm2ppa' missing; assuming package has no files currently installed
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 182466 files and directories currently installed.)
Unpacking openjdk-7-jre-lib (from .../openjdk-7-jre-lib_7u15-2.3.7-0ubuntu1~12.10.1_all.deb) ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: invalid literal/lengths set'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/openjdk-7-jre-lib_7u15-2.3.7-0ubuntu1~12.10.1_all.deb (--unpack):
 cannot copy extracted data for './usr/lib/jvm/java-7-openjdk-common/jre/lib/ext/localedata.jar' to '/usr/lib/jvm/java-7-openjdk-common/jre/lib/ext/localedata.jar.dpkg-new': unexpected end of file or stream
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-7-jre-lib_7u15-2.3.7-0ubuntu1~12.10.1_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of openjdk-7-jre-headless:i386:
 openjdk-7-jre-headless:i386 depends on openjdk-7-jre-lib (= 7u15-2.3.7-0ubuntu1~12.10.1); however:
  Package openjdk-7-jre-lib is not installed.

dpkg: error processing openjdk-7-jre-headless:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-7-jre-headless (>= 7~u3-2.1.1~pre1-1) | java6-runtime-headless; however:
  Package openjdk-7-jre-headless:i386 is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-7-jre-headless:i386 which provides java6-runtime-headless is not configured yet.

dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-7-jre:i386:
 openjdk-7-jre:i386 depends on openjdk-7-jre-headless (= 7u15-2.3.7-0ubuntu1~12.10.1); however:
  Package openjdk-7-jre-headless:i386 is not configured yet.

dpkg: error processing openjdk-7-jre:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-7-jre-jamvm:i386:
 icedtea-7-jre-jamvm:i386 depends on openjdk-7-jre-headless (= 7u15-2.3.7-0ubuntu1~12.10.1); however:
  Package openjdk-7-jre-headless:i386 is not configured yet.

dpkg: error processing icedtea-7-jre-jamvm:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatk-wrapper-java-jni:i386:
 libatk-wrapper-java-jni:i386 depends on default-jre | java2-runtime; however:
  Package default-jre is not installed.
  Package java2-runtime is not installed.
  Package openjdk-7-jre:i386 which provides java2-runtime is not configured yet.

dpkg: error processing libatk-wrapper-java-jni:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatk-wrapper-java:
 libatk-wrapper-java depends on default-jre | java2-runtime; however:
  Package default-jre is not installed.
  Package java2-runtime is not installed.
  Package openjdk-7-jre:i386 which provides java2-runtime is not configured yet.

dpkg: error processing libatk-wrapper-java (--configure):
 dependency problems - leaving unconfigured

And when I go to Updates it shows: 

**[COLOR=#ff0000]The following packages have unmet dependencies:[/COLOR]**
[B][COLOR=#ff0000]
[/COLOR][/B]
**[COLOR=#ff0000]openjdk-7-jre-headless: Depends: openjdk-7-jre-lib (= 7u15-2.3.7-0ubuntu1~12.10.1) but it is not installed[/COLOR]**
**[COLOR=#ff0000]                        Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is installed[/COLOR]**
**[COLOR=#ff0000]                        Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.2-2ubuntu1 is installed[/COLOR]**
[B][COLOR=#ff0000]                        Depends: zlib1g (>= 1:1.1.4) but 1:1.2.7.dfsg-13 is installed

[/COLOR][/B]Any quick solution guys and step by step 
I am totally beginner

---

### Post by slickymaster on 2013-04-08
I'm assuming you were trying to install openjdk-7.

How did you made it? Can you reproduce the steps?

---

### Post by mörgæs on 2013-04-08
As you know
[http://ubuntuforums.org/showthread.php?t=2133275&p=12593105&viewfull=1#post12593105](http://ubuntuforums.org/showthread.php?t=2133275&p=12593105&viewfull=1#post12593105)
we prefer an informative thread title. It helps people in the future which might have the same problem.

Also please stick to standard formatting.

---

### Post by Ali paco on 2013-04-08
I went to Ubuntu software center and i searched for Java package I thought I didn't had Java
And this happened 

What should I do

---

### Post by slickymaster on 2013-04-08
At the terminal run these commands that will purge your system from that bad installation:
```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
```
After that been done lets get Java installed. Run one by one these commands at the terminal:
```
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Edit: Let us know how it went.

---

### Post by deadflowr on 2013-04-08
Please re-read this, especially section 2.

[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

When your review is done try these
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get install -f
```

And you can reply with the outputs.
Use the code tags as suggested in the link:).

---

### Post by Ali paco on 2013-04-08
Thanks guys all of you i really appreciate this

---

