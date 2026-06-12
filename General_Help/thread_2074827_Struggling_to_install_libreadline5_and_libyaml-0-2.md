---
title: "Struggling to install libreadline5 and libyaml-0-2 in Lucid"
date: 2012-10-22
forum: General Help
---

### Post by renegadeandy on 2012-10-22
Hi.

I am trying to follow these instructions : [http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Installation_of_BigBlueButton_0.80](http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Installation_of_BigBlueButton_0.80)

and have got to the install ruby section - and the apt-get install line - copy pasting that results in :

> sudo apt-get install zlib1g-dev libssl-dev libreadline5-dev libyaml-dev build-essential bison checkinstall libffi5 gcc checkinstall libreadline5 libyaml-0-2
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g-dev is already the newest version.
libssl-dev is already the newest version.
E: Couldn't find package libreadline5-dev


Can anyone help me get yaml 0.2 and the dev libreadline packages installed?

---

### Post by dniMretsaM on 2012-10-22
> **renegadeandy said:**
> Hi.

I am trying to follow these instructions : [http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Installation_of_BigBlueButton_0.80](http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu#Installation_of_BigBlueButton_0.80)

and have got to the install ruby section - and the apt-get install line - copy pasting that results in :



Can anyone help me get yaml 0.2 and the dev libreadline packages installed?

The package name is [FONT=Courier New] libreadline-dev[/FONT].

---

### Post by renegadeandy on 2012-10-23
When I do that it doesnt find it :

> andy@help:~$ sudo apt-get install libreadline-dev
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libreadline-dev
andy@help:~$ sudo apt-get install libyaml-0-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libyaml-0-2

---

### Post by dniMretsaM on 2012-10-23
Run these:
```
apt-cache search libreadline
apt-cache search libyaml
```

You should be able to find the correct package name from the results.

---

### Post by renegadeandy on 2012-10-23
It seems i require the specific version 5 of libreadline and version 0-2 of yaml : 

> (Reading database ... 183400 files and directories currently installed.)
Unpacking ruby1.9.2 (from .../ruby1.9.2_1.9.2-p290-1_i386.deb) ...
dpkg: dependency problems prevent configuration of ruby1.9.2:
 ruby1.9.2 depends on libreadline5; however:
  Package libreadline5 is not installed.
 ruby1.9.2 depends on libyaml-0-2; however:
  Package libyaml-0-2 is not installed.
dpkg: error processing ruby1.9.2 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 ruby1.9.2


---

### Post by renegadeandy on 2012-10-24
Any other ideas or should I try asking the big blue button community instead?

---

