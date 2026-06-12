---
title: "IcedTea bin package error"
date: 2007-11-05
forum: General Help
---

### Post by CSMatt on 2007-11-05
I tried to install the IcedTea version of Java (which I assume is the new free implementation of Java) on the Ubuntu 7.10 LiveCD and got this error:
```
Setting up icedtea-java7-bin (7~b21-1.4+20071007-0ubuntu6) ...
/usr/lib/jvm/java-7-icedtea/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing icedtea-java7-bin (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 icedtea-java7-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up icedtea-java7-bin (7~b21-1.4+20071007-0ubuntu6) ...
/usr/lib/jvm/java-7-icedtea/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing icedtea-java7-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 icedtea-java7-bin
```
Any ideas as to what might have went wrong?

---

### Post by dcstar on 2007-11-06
> **CSMatt said:**
> I tried to install the IcedTea version of Java (which I assume is the new free implementation of Java) on the Ubuntu 7.10 LiveCD and got this error:
```
Setting up icedtea-java7-bin (7~b21-1.4+20071007-0ubuntu6) ...
/usr/lib/jvm/java-7-icedtea/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing icedtea-java7-bin (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 icedtea-java7-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up icedtea-java7-bin (7~b21-1.4+20071007-0ubuntu6) ...
/usr/lib/jvm/java-7-icedtea/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing icedtea-java7-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 icedtea-java7-bin
```
Any ideas as to what might have went wrong?

Tell us **exactly** what you did to install this.

---

### Post by CSMatt on 2007-11-06
I just typed
```
sudo aptitude install icedtea-java7-jdk
```
into the terminal after enabling the "universe" repository.  It and all of the other dependencies installed just fine so I omitted them from the description.

---

### Post by CSMatt on 2007-11-07
Not to sound impatient, but can anyone help me here?

---

### Post by bastubis on 2008-05-28
Sorry if this isn't related but I got this at the end of installing ubuntu-restricted-extras (running live persistent from Freecom 8 gig USB databar with Xubuntu 8.04 on eeeC):

Setting up ubuntu-restricted-extras (15) ...
Setting up unrar (1:3.7.8-1) ...

Setting up libaccess-bridge-java (1.22.0-0ubuntu5) ...
Setting up openjdk-6-jre-lib (6b09-0ubuntu2) ...
Setting up openjdk-6-jre-headless (6b09-0ubuntu2) ...
/usr/lib/jvm/java-6-openjdk/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (= 6b09-0ubuntu2); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-gcjwebplugin:
 icedtea-gcjwebplugin depends on openjdk-6-jre (>= 6b06); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea-gcjwebplugin (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-gcjwebplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now got same error installing Skype from Medibunut:
Setting up skype-common (2.0.0.68+repack-0medibuntu3) ...
Setting up skype (2.0.0.68+repack-0medibuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-gcjwebplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Solved by following instructions here to remove open java and installing Sun [http://www.tjansson.dk/?p=125](http://www.tjansson.dk/?p=125) (it's for kubuntu but works on xubuntu) -- seems to be this bug?: [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/224110](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/224110)

---

### Post by aMeR1CaN_aUsSie on 2008-06-15
You might be able to work something out from this:

[http://ubuntuforums.org/showthread.php?t=829866]("http://ubuntuforums.org/showthread.php?t=829866")

aMeR1CaN_aUsSiE

---

