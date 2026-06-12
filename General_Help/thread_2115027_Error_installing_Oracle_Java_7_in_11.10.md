---
title: "Error installing Oracle Java 7 in 11.10"
date: 2013-02-11
forum: General Help
---

### Post by mmistroni on 2013-02-11
HI all
 i am launching this command to install a package useful for ny Nexus development.

sudo apt-get install mtp-tools


But i keep getting the following exception:
```

Do you want to continue [Y/n]? Y
Setting up oracle-java7-installer (7u3-0~eugenesan~oneiric4) ...
Downloading...
--2013-02-11 21:47:32--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com... 217.156.169.209, 217.156.169.192
Connecting to download.oracle.com|217.156.169.209|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2013-02-11 21:47:32--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com... 2.18.218.174
Connecting to edelivery.oracle.com|2.18.218.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2013-02-11 21:47:32--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com|217.156.169.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 1.02M=0.005s

2013-02-11 21:47:32 (1.02 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 oracle-java7-installer
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I thought the problem was in my sources.list, so i used sources list generator from here

[http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)

and i got this

```


#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse 
deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

But i still have the same problem. Could anyone assist me pls?

w/kindest regards
 marco

---

### Post by QIII on 2013-02-11
Please see the Java wiki link in my signature and find the section on dealing with the Eugene San PPA.  It is broken.

Hope it works!

Cheers!

---

