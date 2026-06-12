---
title: "subprocess installed post-installation script returned error exit status 1"
date: 2013-04-20
forum: General Help
---

### Post by AdrianJa on 2013-04-20
hello 
i'm adrian and i'm new at ubuntu this is the first time i am using it and i would like to learn more about it, 
now everytime i try to install a program a window pops out saying that the installation or removal has failed 
and this is what it reads 
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 208050 files and directories currently installed.) 
Removing skype ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Setting up oracle-java7-installer (7u21-0~webupd8~0) ... 
Downloading Oracle Java 7... 
--2013-04-20 13:46:01--  [http://download.oracle.com/otn-pub/java/jdk/7u21-b11/jdk-7u21-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u21-b11/jdk-7u21-linux-i586.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 80.239.149.73, 213.155.152.161 
Connecting to download.oracle.com (download.oracle.com)|80.239.149.73|:80... connected. 
HTTP request sent, awaiting response... 403 Forbidden 
2013-04-20 13:46:02 ERROR 403: Forbidden. 
 
download failed 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 oracle-java7-installer 
Error in function:  
Setting up oracle-java7-installer (7u21-0~webupd8~0) ... 
Downloading Oracle Java 7... 
--2013-04-20 13:46:04--  [http://download.oracle.com/otn-pub/java/jdk/7u21-b11/jdk-7u21-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u21-b11/jdk-7u21-linux-i586.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 80.239.149.73, 213.155.152.161 
Connecting to download.oracle.com (download.oracle.com)|80.239.149.73|:80... connected. 
HTTP request sent, awaiting response... 403 Forbidden 
2013-04-20 13:46:05 ERROR 403: Forbidden. 
 
download failed 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing:
______________________________________________-
Any Ideas ?

---

### Post by Gone fishing on 2013-04-20
How are you trying to install - if you can install using the repostitories do so - probably the openjdk and icedtea packages available in the software center will do what you need, if you need the oracle package then add their repository something like:

[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

---

