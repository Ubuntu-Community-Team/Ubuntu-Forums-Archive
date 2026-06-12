---
title: "Cannot install an app due to Java issues"
date: 2018-02-14
forum: General Help
---

### Post by MobileTechie on 2018-02-14
Trying to install the graphical firewall app GUFW, when I try to install it I get the output below. Seems some problem with Java?

Not sure where to go from here?

Thx

```
root@Microserver:/home/serveradmin# apt-get install gufw                                                                             Reading package lists... Done
Building dependency tree
Reading state information... Done
gufw is already the newest version (16.04.1-0ubuntu1.1).
The following packages were automatically installed and are no longer required:
  libllvm4.0 libllvm4.0:i386 linux-headers-4.10.0-28 linux-headers-4.10.0-28-generic linux-headers-4.13.0-26
  linux-headers-4.13.0-26-generic linux-image-4.10.0-28-generic linux-image-4.13.0-26-generic linux-image-extra-4.10.0-28-generic
  linux-image-extra-4.13.0-26-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 17 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up oracle-java6-installer (6u45-0~webupd8~8) ...
Downloading Oracle Java 6...
--2018-02-14 13:18:21--  [http://download.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin](http://download.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin)
Resolving download.oracle.com (download.oracle.com)... 88.221.40.92
Connecting to download.oracle.com (download.oracle.com)|88.221.40.92|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin](https://edelivery.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin) [following]
--2018-02-14 13:18:26--  [https://edelivery.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin](https://edelivery.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.195.113.74, 2a02:26f0:13b:387::2d3e, 2a02:26f0:13b:39f::2d3e
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.195.113.74|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin?AuthParam=1518614431_32e91a5a82f24727cd5779bceb156bf5](http://download.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin?AuthParam=1518614431_32e91a5a82f24727cd5779bceb156bf5) [following]
--2018-02-14 13:18:31--  [http://download.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin?AuthParam=1518614431_32e91a5a82f24727cd5779bceb156bf5](http://download.oracle.com/otn-pub/java/jdk/6u45-b06/jdk-6u45-linux-x64.bin?AuthParam=1518614431_32e91a5a82f24727cd5779bceb156bf5)
Connecting to download.oracle.com (download.oracle.com)|88.221.40.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2018-02-14 13:18:33 ERROR 404: Not Found.


download failed
Oracle JDK 6 is NOT installed.
dpkg: error processing package oracle-java6-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java6-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Microserver:/home/serveradmin#
```

---

### Post by QIII on 2018-02-14
Hello.

As far as I know, Oracle has withdrawn Java 6 from their downloads due to its massive security issues.

Since it appears you have used webupd8 to install it, I'd suggest going there, following Andrei's instructions for uninstalling and then installing 7, 8 or 9.

---

