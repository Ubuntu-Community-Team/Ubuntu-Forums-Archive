---
title: "Errors with dpkg when trying to install Javac java compiler"
date: 2019-11-23
forum: General Help
---

### Post by retsek2 on 2019-11-23
I am trying to install javac by typing 

sudo apt install default-jdk

into my terminal but I receive the error

Setting up oracle-java11-installer-local (11.0.5-1~linuxuprising0) ...
Before installing this package,
please download the Oracle JDK 11 .tar.gz file
with the same version as this package (version 11.0.4),
and place it in /var/cache/oracle-jdk11-installer-local,

E.g.:
sudo mkdir -p /var/cache/oracle-jdk11-installer-local
sudo cp jdk-11.0.4_linux-x64_bin.tar.gz /var/cache/oracle-jdk11-installer-local/
sha256sum mismatch jdk-11.0.5_linux-x64_bin.tar.gz
Oracle JDK 11 is NOT installed.
dpkg: error processing package oracle-java11-installer-local (--configure):
 installed oracle-java11-installer-local package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of default-jdk:
 default-jdk depends on openjdk-11-jdk; however:
  Package openjdk-11-jdk is not installed.
  Package oracle-java11-installer-local which provides openjdk-11-jdk is not configured yet.

dpkg: error processing package default-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of default-jdk-headless:
 default-jdk-headless depends on openjdk-11-jdk-headless; however:
  Package openjdk-11-jdk-headless is not installed.
  Package oracle-java11-installer-local which provides openjdk-11-jdk-headless is not configured yet.

dpkg: error processing package default-jdk-headless (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                   Errors were encountered while processing:
 oracle-java11-installer-local
 default-jdk
 default-jdk-headless
E: Sub-process /usr/bin/dpkg returned an error code (1)

pls I just wanna do Java

---

### Post by TheFu on 2019-11-25
There are multiple variants of javac.  Do you care which one gets installed?
```
The program 'javac' can be found in the following packages:
 * default-jdk (You will have to enable component called 'main')
 * ecj (You will have to enable component called 'main')
 * gcj-5-jdk (You will have to enable component called 'main')
 * openjdk-8-jdk-headless (You will have to enable component called 'main')
 * gcj-4.8-jdk (You will have to enable component called 'universe')
 * gcj-4.9-jdk (You will have to enable component called 'universe')
 * openjdk-9-jdk-headless (You will have to enable component called 'universe')
```

So, install one of those packages.  I would avoid the Oracle versions and choose the openjdk-9-jdk-headless, but you might have different requirements.  Also, I'm on 16.04, so your release might have different versions of java.

"just doing java" isn't a trivial thing.  If you search for "ubuntu 18.04 java install", I bet you'll find very detailed instructions.  You've probably already found some.

---

### Post by tors on 2019-11-26
One thing that comes to my mind while reading the output,
is that it asks for version 11.0.4,
and the checksum fails with a filename which has 11.0.5.

So some kind of mismatch there...

> ...
please download the Oracle JDK 11 .tar.gz file
with the same version as this package (version 11.0.4),
...

...
sha256sum mismatch jdk-11.0.5_linux-x64_bin.tar.gz
...

---

