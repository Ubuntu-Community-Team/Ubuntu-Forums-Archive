---
title: "Oracle Java Update Problem"
date: 2017-01-20
forum: General Help
---

### Post by Thiras on 2017-01-20
Hi,

I'm using ppa:webupd8team/java for Oracle's Java 8 on Ubuntu 16.04. There was no problem until get update few days ago. Now all apt operations dump lots of errors. I couldn't find any useful info on the web. Here is the dump

```
sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up oracle-java8-installer (8u121-1~webupd8~0) ...
Using wget settings from /var/cache/oracle-jdk8-installer/wgetrc
Downloading Oracle Java 8...
--2017-01-20 19:09:40--  http://download.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 212.252.126.27, 212.252.126.57
Connecting to download.oracle.com (download.oracle.com)|212.252.126.27|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.tar.gz [following]
--2017-01-20 19:09:40--  https://edelivery.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.221.185.251, 2a02:26f0:c000:186::2d3e, 2a02:26f0:c000:183::2d3e
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.221.185.251|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.tar.gz?AuthParam=1484928701_94fbed365783298918b1ac116fc727de [following]
--2017-01-20 19:09:41--  http://download.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.tar.gz?AuthParam=1484928701_94fbed365783298918b1ac116fc727de
Connecting to download.oracle.com (download.oracle.com)|212.252.126.27|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-8u121-linux-x64.tar.gz
Oracle JDK 8 is NOT installed.
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-java8-set-default:
 oracle-java8-set-default depends on oracle-java8-installer; however:
  Package oracle-java8-installer is not configured yet.

dpkg: error processing package oracle-java8-set-default (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 oracle-java8-installer
 oracle-java8-set-default
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It says Oracle Java is NOT installed. But I'm pretty sure it's installed and working without any problem.

---

### Post by Thiras on 2017-01-20
Problem solved after removing cached java at /var/cache/oracle-jdk8-installer

Probably hash mismatch as it says.

---

