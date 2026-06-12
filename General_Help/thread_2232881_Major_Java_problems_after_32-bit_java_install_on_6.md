---
title: "Major Java problems after 32-bit java install on 64-bit ubuntu"
date: 2014-07-04
forum: General Help
---

### Post by regnumimbriumx on 2014-07-04
Hi All,

I'm currently using a 64-bit 14.04, but an online class that I'm taking wouldn't correctly load its Java components. After I fixed the same problem on my 64-bit windows by installing 32-bit Java, I decided to try for the same fix on my ubuntu machine.

After following many different install/uninstall guides, I've really trashed my Java installation. Reformatting the machine is an option, but at this level of experience with ubuntu, I'm really getting tired of reformatting ubuntu every single time something gets screwed up. Can anyone help me keep the ubunt faith by providing a solution? Here's the output I get from apt-get -f install:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libice-dev:i386 libpthread-stubs0-dev:i386 libsm-dev:i386 libx11-dev:i386
  libx11-doc libxau-dev:i386 libxcb1-dev:i386 libxdmcp-dev:i386 libxt-dev:i386
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools
  xtrans-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
8 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up openjdk-6-jre-headless:amd64 (6b31-1.13.3-1ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java doesn't exist
dpkg: error processing package openjdk-6-jre-headless:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up openjdk-6-jre-headless:i386 (6b31-1.13.3-1ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java doesn't exist
dpkg: error processing package openjdk-6-jre-headless:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:amd64:
 icedtea-6-jre-cacao:amd64 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:amd64 is not configured yet.


dpkg: error processing package icedtea-6-jre-cacao:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:i386:
 icedtea-6-jre-cacao:i386 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:i386 is not configured yet.


dpkg: error processing package icedtea-6-jre-cacao:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm:amd64:
 icedtea-6-jre-jamvm:amd64 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:amd64 is not configured yet.


dpkg: error processing package icedtea-6-jre-jamvm:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm:i386:
 icedtea-6-jre-jamvm:i386 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:i386 is not configured yet.


dpkg: error processing package icedtea-6-jre-jamvm:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of openjdk-6-jre:i386:
 openjdk-6-jre:i386 depends on openjdk-6-jre-headless (>= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:i386 is not configured yet.


dpkg: error processing package openjdk-6-jre:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icedtea-6-plugin:i386:
 icedtea-6-plugin:i386 depends on openjdk-6-jre; however:
  Package openjdk-6-jre:i386 is not configured yet.


dpkg: error processing package icedtea-6-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Issuing dpkg --configure -a yields:
```

Setting up openjdk-6-jre-headless:amd64 (6b31-1.13.3-1ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java doesn't exist
dpkg: error processing package openjdk-6-jre-headless:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up openjdk-6-jre-headless:i386 (6b31-1.13.3-1ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java doesn't exist
dpkg: error processing package openjdk-6-jre-headless:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:i386:
 openjdk-6-jre:i386 depends on openjdk-6-jre-headless (>= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:i386 is not configured yet.


dpkg: error processing package openjdk-6-jre:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:amd64:
 icedtea-6-jre-cacao:amd64 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:amd64 is not configured yet.


dpkg: error processing package icedtea-6-jre-cacao:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:i386:
 icedtea-6-jre-cacao:i386 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:i386 is not configured yet.


dpkg: error processing package icedtea-6-jre-cacao:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-plugin:i386:
 icedtea-6-plugin:i386 depends on openjdk-6-jre; however:
  Package openjdk-6-jre:i386 is not configured yet.


dpkg: error processing package icedtea-6-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm:amd64:
 icedtea-6-jre-jamvm:amd64 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:amd64 is not configured yet.


dpkg: error processing package icedtea-6-jre-jamvm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm:i386:
 icedtea-6-jre-jamvm:i386 depends on openjdk-6-jre-headless (= 6b31-1.13.3-1ubuntu1); however:
  Package openjdk-6-jre-headless:i386 is not configured yet.


dpkg: error processing package icedtea-6-jre-jamvm:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-6-jre-headless:amd64
 openjdk-6-jre-headless:i386
 openjdk-6-jre:i386
 icedtea-6-jre-cacao:amd64
 icedtea-6-jre-cacao:i386
 icedtea-6-plugin:i386
 icedtea-6-jre-jamvm:amd64
 icedtea-6-jre-jamvm:i386

```

At the very least, I'd like to get Java functional, again. Best case scenario would be to get a 32-bit package working on my 64-bit distro.

THANKS!!!

---

### Post by slickymaster on 2014-07-04
From [here]("http://askubuntu.com/questions/84483/how-to-completely-uninstall-java"):

Remove all the Java related packages (Sun, Oracle, OpenJDK, IcedTea plugins, GIJ):
```
sudo apt-get update
apt-cache search java | awk '{print($1)}' | grep -E -e '^(ia32-)?(sun|oracle)-java' -e '^openjdk-' -e '^icedtea' -e '^(default|gcj)-j(re|dk)' -e '^gcj-(.*)-j(re|dk)' -e 'java-common' | xargs sudo apt-get -y remove
sudo apt-get -y autoremove
```
Purge config files:
```
dpkg -l | grep ^rc | awk '{print($2)}' | xargs sudo apt-get -y purge
```
Remove Java config and cache directory:
```
sudo bash -c 'ls -d /home/*/.java' | xargs sudo rm -rf
```
Remove manually installed JVMs:
```
sudo rm -rf /usr/lib/jvm/*
```

---

### Post by regnumimbriumx on 2014-07-04
Thank you for your response, slicky. I believe that I had recently tried that series of commands, to no avail. At any rate, I was able to fix the problem by manually removing a lone amd64 java package. Once that was gone, it allowed for the full removal and reinstallation of the 32 bit variants. My java is now working as desired :)

---

