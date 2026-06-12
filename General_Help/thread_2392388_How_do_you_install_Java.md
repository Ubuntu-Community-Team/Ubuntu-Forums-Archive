---
title: "How do you install Java"
date: 2018-05-20
forum: General Help
---

### Post by icebunny08 on 2018-05-20
I am currently having a problem, as a new Ubuntu user, I do not know what to do. I don't get the instructions in the official website, and unlike the one for MacOS and Windows, It does not have an installer. Please help me because I really want to code again because it's almost the start of classes. :confused:

---

### Post by Perfect Storm on 2018-05-20
Oracle java?

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
javac -version
```

---

### Post by icebunny08 on 2018-05-21
It says, "Oracle JDK 8 is NOT installed." and it also says:
dpkg: error processing package oracle-java8-installer (--configure):
 installed oracle-java8-installer package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Perfect Storm on 2018-05-21
Try with
```
sudo apt install oracle-java8-set-default
```

instead.

[https://linuxconfig.org/how-to-install-java-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-java-on-ubuntu-18-04-bionic-beaver-linux)

---

### Post by icebunny08 on 2018-05-21
Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-8u171-linux-x64.tar.gz
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 installed oracle-java8-installer package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

I get this.

---

