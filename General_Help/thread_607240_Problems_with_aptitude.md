---
title: "Problems with aptitude"
date: 2007-11-08
forum: General Help
---

### Post by jgoguen on 2007-11-08
I'm having problems with apt-get constantly offering the same package for upgrade.  This is off a personal repo so I'm not sure if it's a problem with the repo or not.  I have added this line to my /etc/apt/sources.list:
```
deb http://jgoguen.ca/repo mercury release release-lite pre-release pre-release-lite
```This makes available the packages 'mercury-messenger' (from release/pre-release) and 'mercury-messenger-lite' (from release-lite/pre-release-lite).  In the pre-release and pre-release-lite sections, the latest available version is 1.9RC11.  In the release and release-lite sections, the latest available version is 1:1.9.  If I install mercury-messenger-lite from release-lite (or upgrade, where the previous version would be 1.9RC11 from pre-release-lite) everything is fine.  If, however, I install mercury-messenger from release (or upgrade, where the previous version would be 1.9RC11 from pre-release) I immediately get told that I need to update mercury-messenger from 1:1.9 to 1:1.9.  Here is what I get before installing each package from apt-cache policy:
```
[jgoguen@hermes:~]$ apt-cache policy mercury-messenger
mercury-messenger:
  Installed: (none)
  Candidate: 1:1.9
  Version table:
     1:1.9 0
        500 http://jgoguen.ca mercury/release Packages
     1.9RC11 0
        500 http://jgoguen.ca mercury/pre-release Packages
[jgoguen@hermes:~]$ apt-cache policy mercury-messenger-lite
mercury-messenger-lite:
  Installed: (none)
  Candidate: 1:1.9
  Version table:
     1:1.9 0
        500 http://jgoguen.ca mercury/release-lite Packages
     1.9RC11 0
        500 http://jgoguen.ca mercury/pre-release-lite Packages
```Here is what it looks like after installing each package:
```
mercury-messenger:
  Installed: 1:1.9
  Candidate: 1:1.9
  Version table:
     1:1.9 0
        500 http://jgoguen.ca mercury/release Packages
 *** 1:1.9 0
        100 /var/lib/dpkg/status
     1.9RC11 0
        500 http://jgoguen.ca mercury/pre-release Packages
[jgoguen@hermes:~]$ apt-cache policy mercury-messenger-lite 
mercury-messenger-lite:
  Installed: 1:1.9
  Candidate: 1:1.9
  Version table:
 *** 1:1.9 0
        500 http://jgoguen.ca mercury/release-lite Packages
        100 /var/lib/dpkg/status
     1.9RC11 0
        500 http://jgoguen.ca mercury/pre-release-lite Packages
```These packages cannot be installed together, so between installs I used 'sudo apt-get remove --purge' to uninstall.

Here is the relevant section of /var/lib/dpkg/status with each installed:
```
mercury-messenger-lite installed:
Package: mercury-messenger
Status: purge ok not-installed
Priority: optional

Package: mercury-messenger-lite
Status: install ok installed
Priority: optional
Section: contrib/net
Installed-Size: 9608
Maintainer: Danny, Joel Goguen (jgoguen) <jtgoguen@gmail.com>
Architecture: all
Version: 1:1.9
Recommends: sun-java5-bin | sun-java6-bin
Description: Messenger for the MSN protocol made by Danny
 Mercury is a MSN client supporting both the MSN protocol and the Jabber
 protocol.  Mercury has the capabilities of MSN7, MSN8, and others.  Mercury
 also features a RSS reader
``````
mercury-messenger installed:
Package: mercury-messenger
Status: install ok installed
Priority: optional
Maintainer: Vicente Virla <vicentevirla@gmail.com>
Architecture: all
Version: 1:1.9
Description: Messenger for the MSN protocol made by Danny

Package: mercury-messenger-lite
Status: purge ok not-installed
Priority: optional
Section: contrib/net
```Does anyone know how I would allow installation of mercury-messenger and get rid of this continual upgrade cycle?

---

### Post by dcstar on 2007-11-08
> **jgoguen said:**
> 
.........
]Does anyone know how I would allow installation of mercury-messenger and get rid of this continual upgrade cycle?

Simply go into Synaptic and use the "Lock Version" function.

---

### Post by jgoguen on 2007-11-09
Unfortunately that means remembering to unlock once the next update is out :)  I suppose I shall just have to tell everyone to remember to unlock the version once the next update is available.

Thanks :)

---

