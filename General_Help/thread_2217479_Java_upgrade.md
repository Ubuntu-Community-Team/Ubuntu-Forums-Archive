---
title: "Java upgrade"
date: 2014-04-17
forum: General Help
---

### Post by Ri_CatB_Support on 2014-04-17
Hi All,

We tried upgrading Java 1.7 on ubuntu 10.04 on our test server. we are unable to upgrade the version.

Below are message we were getting while upgrading: download failed
:/$ sudo aptitude install oracle-java7-installer
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following partially installed packages will be configured:
  oracle-java7-installer
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up oracle-java7-installer (7u55-0~webupd8~0) ...
Downloading Oracle Java 7...
--2014-04-17 17:05:17--  [http://download.oracle.com/otn-pub/java/jdk/7u55-b13/jdk-7u55-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u55-b13/jdk-7u55-linux-x64.tar.gz)
Connecting to 10.76.122.33:80... failed: No route to host.
download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up oracle-java7-installer (7u55-0~webupd8~0) ...
Downloading Oracle Java 7...
--2014-04-17 17:05:21--  [http://download.oracle.com/otn-pub/java/jdk/7u55-b13/jdk-7u55-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u55-b13/jdk-7u55-linux-x64.tar.gz)
Connecting to 10.76.122.33:80... failed: Connection timed out.
Retrying.
--2014-04-17 17:05:43--  (try: 2)  [http://download.oracle.com/otn-pub/java/jdk/7u55-b13/jdk-7u55-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u55-b13/jdk-7u55-linux-x64.tar.gz)
Connecting to 10.76.122.33:80... failed: No route to host.
download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information


Could anyone please help me to resolve this issue.

Thanks,
Prakash

---

### Post by Cavsfan on 2014-04-17
Get Java 8 from Web UPD8 in my signature. It auto updates itself.

---

