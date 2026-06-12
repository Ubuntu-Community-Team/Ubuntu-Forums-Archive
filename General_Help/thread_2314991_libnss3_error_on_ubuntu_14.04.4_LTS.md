---
title: "libnss3 error on ubuntu 14.04.4 LTS"
date: 2016-02-25
forum: General Help
---

### Post by satriaf on 2016-02-25
I can't install/remove/resolve the problem caused by libnss3 on my ubuntu 14.04.4 LTS. At the beginning I got a problem on Upwork time tracker (Connection failed) then I followed the steps on this link:[https://gist.github.com/alexda14/d0632aed2fbf86c6fee1](https://gist.github.com/alexda14/d0632aed2fbf86c6fee1). then the libnss3 packages messed up my machine. It says 'Error:BrokenCount > 0. this usually means that your installed packages have unmet dependencies'. I've tried everything to solve the conflicts issued but fail.

```
sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libnss3-1d:i386      Network Security Service libraries - transitional package
 libnss3:i386         Network Security Service libraries

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 libnss3:amd64        Network Security Service libraries
```

then

```
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libnss3-1d:i386:
 libnss3-1d:i386 depends on libnss3 (= 2:3.21-0ubuntu0.14.04.1); however:
  Version of libnss3:i386 on system is 2:3.19.2-1ubuntu1.

dpkg: error processing package libnss3-1d:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing package libnss3:amd64 (--configure):
 package libnss3:amd64 2:3.21-0ubuntu0.14.04.1 cannot be configured because libnss3:i386 is at a different version (2:3.19.2-1ubuntu1)
dpkg: error processing package libnss3:i386 (--configure):
 package libnss3:i386 2:3.19.2-1ubuntu1 cannot be configured because libnss3:amd64 is at a different version (2:3.21-0ubuntu0.14.04.1)
Errors were encountered while processing:
 libnss3-1d:i386
 libnss3:amd64
 libnss3:i386

```

Remove
```
sudo apt-get remove --auto-remove libnss3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 brackets : Depends: libnss3 (>= 3.12.6) but it is not going to be installed
 evolution-data-server : Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                                  libnss3-1d (>= 3.12.0~beta3) but it is not going to be installed
 flashplugin-installer : Depends: libnss3 but it is not going to be installed
 gitkraken : Depends: libnss3 but it is not going to be installed
 google-chrome-stable : Depends: libnss3 (>= 3.14.3) but it is not going to be installed
 libcamel-1.2-45 : Depends: libnss3 (>= 2:3.14) but it is not going to be installed
 libnm-util2 : Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                        libnss3-1d (>= 3.12.0~1.9b1) but it is not going to be installed
 libnss3-1d:i386 : Depends: libnss3:i386 (= 2:3.21-0ubuntu0.14.04.1) but 2:3.19.2-1ubuntu1 is to be installed
 libnss3-nssdb : Depends: libnss3 (= 2:3.21-0ubuntu0.14.04.1) but it is not going to be installed
 liboauth0 : Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                      libnss3-1d (>= 3.12.0~1.9b1) but it is not going to be installed
 liboxideqtcore0 : Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                            libnss3-1d (>= 3.12.4) but it is not going to be installed
 libpurple0 : Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                       libnss3-1d (>= 3.12.0~1.9b1) but it is not going to be installed
 libreoffice-core : Depends: libnss3 (>= 2:3.13.4-2~) but it is not going to be installed or
                             libnss3-1d (>= 3.12.0~1.9b1) but it is not going to be installed
 upwork : Depends: libnss3 (>= 2:3.14.3) but it is not going to be installed or
                   libnss3 (>= 3.14.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Check
```
sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libnss3 : Breaks: libnss3:i386 (!= 2:3.21-0ubuntu0.14.04.1) but 2:3.19.2-1ubuntu1 is installed
 libnss3:i386 : Breaks: libnss3 (!= 2:3.19.2-1ubuntu1) but 2:3.21-0ubuntu0.14.04.1 is installed
 libnss3-1d:i386 : Depends: libnss3:i386 (= 2:3.21-0ubuntu0.14.04.1) but 2:3.19.2-1ubuntu1 is installed
E: Unmet dependencies. Try using -f.
```

Install
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  acpi gnome-desktop-data gnumeric-common gnumeric-doc libantlr-java
  libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcommons-validator-java
  libdoxia-sitetools-java libgegl-0.2-0 libgoffice-0.10-10-common
  libjavascriptcoregtk-1.0-0 libjdependency-java libjtidy-java
  libmaven-archiver-java libmaven-clean-plugin-java
  libmaven-compiler-plugin-java libmaven-dependency-tree-java
  libmaven-filtering-java libmaven-install-plugin-java
  libmaven-jar-plugin-java libmaven-plugin-tools-java
  libmaven-reporting-impl-java libmaven-resources-plugin-java
  libmaven-shade-plugin-java libming1 libplexus-compiler-java
  libplexus-digest-java libplexus-velocity-java libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwerken.xpath-java libxml-xpathengine-perl
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic-tuxonice
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.13.0-76-generic-tuxonice linux-image-3.19.0-25-generic
  linux-image-extra-3.13.0-76-generic-tuxonice
  linux-image-extra-3.19.0-25-generic linux-tools-3.13.0-76
  linux-tools-3.13.0-76-generic tclx8.4 velocity
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnss3:i386
The following packages will be upgraded:
  libnss3:i386
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1.066 kB of archives.
After this operation, 435 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 443812 files and directories currently installed.)
Preparing to unpack .../libnss3_2%3a3.21-0ubuntu0.14.04.1_i386.deb ...
Unpacking libnss3:i386 (2:3.21-0ubuntu0.14.04.1) over (2:3.19.2-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libnss3_2%3a3.21-0ubuntu0.14.04.1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libnss3/changelog.Debian.gz', which is different from other instances of package libnss3:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libnss3_2%3a3.21-0ubuntu0.14.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is also affect Ubuntu Software Center with this message: 'New software can't be installed,...'.. I can't install/remove any software. repair don't work!

---

### Post by satriaf on 2016-02-25
Okay. I managed to fix my problem. Actually it my own mistakes. I have 64bit ubuntu but installed libnss3 for i386. 
apt-cache policy libnss3*
to find out all libnss3 dependencies then purge them:
sudo apt-get purge libnss3-1d:i386 libnss3-nssdb:i386 libnss3-1d-dbg:i386 libnss3-dbg:i386 libnss3:i386 libnss3-dev:i386 libnss3-tools:i386

---

