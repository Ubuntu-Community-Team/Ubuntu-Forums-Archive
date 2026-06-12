---
title: "Java error whn installing anything."
date: 2015-07-29
forum: General Help
---

### Post by roadwarrior2 on 2015-07-29
Whenever I try to update or install anything the my server always tries to install Oracle Java and fails. I am using Ubuntu Server 14.04 and this is the message:

```
Setting up oracle-java8-installer (8u45+8u33arm-1~webupd8~1) ...
Downloading Oracle Java 8...
--2015-07-29 07:38:38--  http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 23.217.138.98, 23.217.138.43
Connecting to download.oracle.com (download.oracle.com)|23.217.138.98|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz [following]
--2015-07-29 07:38:38--  https://edelivery.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 172.226.99.109
Connecting to edelivery.oracle.com (edelivery.oracle.com)|172.226.99.109|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz?AuthParam=1438173638_e6df8410ccb7d73da4b7b5de524755f1 [following]
--2015-07-29 07:38:38--  http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz?AuthParam=1438173638_e6df8410ccb7d73da4b7b5de524755f1
Connecting to download.oracle.com (download.oracle.com)|23.217.138.98|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-8u45-linux-x64.tar.gz
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QIII on 2015-07-29
Hello!

Try uninstalling the installer completely first.

```
sudo apt-get purge oracle-java8-installer 
```

Do you need Java on the server?  Did you add the webupd8 PPA?

---

