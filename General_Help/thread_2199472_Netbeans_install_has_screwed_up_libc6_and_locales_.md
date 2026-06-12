---
title: "Netbeans install has screwed up libc6 and locales dependencies"
date: 2014-01-14
forum: General Help
---

### Post by rahul8590 on 2014-01-14
I was trying to install netbeans in my system using 

> $sudo apt-get install netbeans 

it has updates libc6 and locales and after that, I keep getting locales configuration error all the time. 

The following updates happened 


> Start-Date: 2014-01-14  03:14:34
Commandline: apt-get install netbeans
// A lot of packages are listed  which I m not showing in here. I have attached that data in dep_list.txt incase you want to see them.
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2014-01-14  03:15:05


Start-Date: 2014-01-14  03:27:45
Commandline: apt-get install -f
Upgrade: locales:i386 (2.13+git20120306-3, 2.17-97)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2014-01-14  03:27:45


Start-Date: 2014-01-14  03:34:53
Commandline: apt-get -f install
Upgrade: locales:i386 (2.13+git20120306-3, 2.17-97)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2014-01-14  03:34:53





Everytime I try to fix the umnet dependencies, I get the following error 

> rahul@g3ck0:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  jsvc python-dirspec golang-doc libax25 gtk2-engines-pixbuf python-sqlalchemy handlersocket-doc
  python-sqlalchemy-ext python-utidylib python-html2text python-beautifulsoup python-pyside.qtcore
  libshiboken1.1 libtidy-0.99-0 python-unity-singlet python-oauth2 python-feedparser openbsd-inetd
  python-regex libcommons-daemon-java python-pysqlite2 python-pyside.qtnetwork libpyside1.1 libodbc1
  python-magic python-pyside.qtgui python-pyside.qtwebkit
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  locales
The following packages will be upgraded:
  locales
1 upgraded, 0 newly installed, 0 to remove and 1949 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,845 kB of archives.
After this operation, 6,735 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of locales:
 libc6 (2.17-97) breaks locales (<< 2.17) and is installed.
  Version of locales to be configured is 2.13+git20120306-3.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)
 

How do I resolve this ? I guess libc6 seems to be a very important package , I m not sure about locales though.  I am still quite baffled on how this happened in the first place. If there is some error while installation, none of the packages should have been installed / activated . But it seems like there has been partial installation. 

The following is my ubuntu version

> rahul@g3ck0:/var/cache/apt/archives$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"


---

