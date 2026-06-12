---
title: "Can't install any tar.gz, .deb etc. from terminal and commands dont work"
date: 2015-11-02
forum: General Help
---

### Post by arthurz12345 on 2015-11-02
when i try to install virtualbox 5.0.8 on ubuntu 14.04 on terminal, it looks like it'll work, but then there's the error: 
Errors were encountered while processing:
 virtualbox-5.0

heres the whole thing:
user@system-68e26d:~/Desktop$ sudo dpkg -i virtualbox-5.0_5.0.8-103449-Ubuntu-trusty_i386.deb
(Reading database ... 204321 files and directories currently installed.)
Preparing to unpack virtualbox-5.0_5.0.8-103449-Ubuntu-trusty_i386.deb ...
Unpacking virtualbox-5.0 (5.0.8-103449~Ubuntu~trusty) over (5.0.8-103449~Ubuntu~trusty) ...
dpkg: dependency problems prevent configuration of virtualbox-5.0:
 virtualbox-5.0 depends on psmisc; however:


dpkg: error processing package virtualbox-5.0 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Errors were encountered while processing:
 virtualbox-5.0

Can you help me?  Thx.  PS I've also tried using the root terminal and that didn't do anything

specs:
acer travelmate b115
cpu: 2.16 ghz intel celeron n2380 dual core
ram: 4gb
linux kernel: 3.16.0-38 generic
graphicscard: intel valleyview gen7
32 bit

---

### Post by ian-weisser on 2015-11-02
> **arthurz12345 said:**
> 
Preparing to unpack virtualbox-5.0_5.0.8-103449-Ubuntu-trusty_i386.deb ...
Unpacking virtualbox-5.0 (5.0.8-103449~Ubuntu~trusty) over (5.0.8-103449~Ubuntu~trusty) ...
dpkg: **dependency problems** prevent configuration of virtualbox-5.0:
 virtualbox-5.0 depends on **psmisc**; however:

Important information is usually after the 'however:' It would help. 
Dependency problems cannot be resolved by forcing through the root terminal. They must be *solved*.
Please show us the entire output of:
```
apt-cache policy psmisc
```

---

### Post by arthurz12345 on 2015-11-02
user@system-68e26d:~$ apt-cache policy psmisc
psmisc:
  Installed: 22.20-1ubuntu2
  Candidate: 22.20-1ubuntu2
  Version table:
 *** 22.20-1ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by deadflowr on 2015-11-03
How sure are you that you are running a 32-bit version of Ubuntu?

---

### Post by arthurz12345 on 2015-11-03
Sorry i just checked and its actually 64 bit.  Maybe it was a conincidence that the 32 bit stuff worked

---

