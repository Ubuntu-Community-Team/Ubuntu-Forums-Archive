---
title: "Removing Oracle JDK11"
date: 2020-07-13
forum: General Help
---

### Post by arjun13 on 2020-07-13
Hey Guys, I am using Ubuntu 20.04 amd64 and was trying to install Oracle JDK 11 using the tutorial:
[https://www.infoworld.com/article/3514725/installing-oracle-java-se-11-on-ubuntu-18-04.html](https://www.infoworld.com/article/3514725/installing-oracle-java-se-11-on-ubuntu-18-04.html)

However, I now don't want it and have removed the "/var/cache/oracle-jdk11-installer-local/" directory and have also removed:
"sudo add-apt-repository ppa:linuxuprising/java" using apt.

However, when I execute the command:

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up oracle-java11-installer-local (11.0.7-1~linuxuprising0) ...
Before installing this package,
please download the Oracle JDK 11 .tar.gz file
with the same version as this package (version 11.0.4),
and place it in /var/cache/oracle-jdk11-installer-local,

E.g.:
sudo mkdir -p /var/cache/oracle-jdk11-installer-local
sudo cp jdk-11.0.4_linux-x64_bin.tar.gz /var/cache/oracle-jdk11-installer-local/
sha256sum mismatch jdk-11.0.7_linux-x64_bin.tar.gz
Oracle JDK 11 is NOT installed.
dpkg: error processing package oracle-java11-installer-local (--configure):
 installed oracle-java11-installer-local package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 oracle-java11-installer-local
E: Sub-process /usr/bin/dpkg returned an error code (1)


How to solve this?

Thanks!

---

### Post by TheFu on 2020-07-15
It appears you broke your APT by doing things in the wrong way.  The solution is to put things back and the output above has the suggested solution.
To remove a package that is known to APT, you must use APT tools - apt, apt-get, aptitude, syntapic ... one of those.  Remove and purge it, then clean up the repos that were added, then update+upgrade.

Until you do these things, the APT system will be confused and probably refuse to update.

---

