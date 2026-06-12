---
title: "NX installation"
date: 2006-10-09
forum: General Help
---

### Post by mukatira on 2006-10-09
HI all,

I installed nx following the instructions from [http://www.nomachine.com/ar/view.php?ar_id=AR07D00407](http://www.nomachine.com/ar/view.php?ar_id=AR07D00407)

When I test it: I get the follwing error.

**@SM-ubuntu:/usr/NX/bin$ ./nxserver --status**
NX> 595 ERROR: Initialization failed: Can't open file: /usr/NX/etc/server.cfg.
NX> 595 ERROR: No such file or directory. Please try to fix the problem by
NX> 595 ERROR: running /usr/NX/scripts/setup/nxserver --install.

Could anyone point me to what I am doing wrong?
Thanks

-Sm

Here are the errors during installation:

**@SM-ubuntu:~/Desktop$ sudo dpkg -i force-architecture nxclient_2.1.0-6_i386.deb**
dpkg: error processing force-architecture (--install):
cannot access archive: No such file or directory
Selecting previously deselected package nxclient.
(Reading database ... 80576 files and directories currently installed.)
Unpacking nxclient (from nxclient_2.1.0-6_i386.deb) ...
dpkg: dependency problems prevent configuration of nxclient:
nxclient depends on libstdc++2.10-glibc2.2; however:
Package libstdc++2.10-glibc2.2 is not installed.
dpkg: error processing nxclient (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
force-architecture
nxclient
**@SM-ubuntu:~/Desktop$ sudo dpkg -i force-architecture nxnode_2.1.0-7_i386.deb**
dpkg: error processing force-architecture (--install):
cannot access archive: No such file or directory
Selecting previously deselected package nxnode.
(Reading database ... 80716 files and directories currently installed.)
Unpacking nxnode (from nxnode_2.1.0-7_i386.deb) ...
dpkg: dependency problems prevent configuration of nxnode:
nxnode depends on nxclient (>= 2.1.0); however:
Package nxclient is not configured yet.
dpkg: error processing nxnode (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
force-architecture
nxnode
**@SM-ubuntu:~/Desktop$ sudo dpkg -i force-architect nxserver_2.1.0-7_i386.deb**
dpkg: error processing force-architect (--install):
cannot access archive: No such file or directory
Selecting previously deselected package nxserver.
(Reading database ... 80921 files and directories currently installed.)
Unpacking nxserver (from nxserver_2.1.0-7_i386.deb) ...
dpkg: dependency problems prevent configuration of nxserver:
nxserver depends on nxclient (>= 2.1.0); however:
Package nxclient is not configured yet.
nxserver depends on nxnode (>= 2.1.0); however:
Package nxnode is not configured yet.
dpkg: error processing nxserver (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
force-architect
nxserver

---

### Post by craig.brisbane on 2006-11-25
Hi, I'm very new to linux - I have been getting the same error message as you when trying to install NXclient - did you have any luck getting it to work? If so what did you do?

Ta
Craig

---

### Post by Macchi on 2006-11-28
The folowing worked for me: 
```
sudo apt-get -f install
```
Then issue againg the command:
sudo dpkg -i <node>.deb <server>.deb <client>.deb
with the latest package names. This solved the installation problem for me.

Unfortunately I am now experiencing others problems with the anti-aliasing of fonts. NX worked flawlessly on my systems with the third-party repositories but later I had to rely directly on the packages provided by Nomachine. Unfortunately they seem to be less stable.

---

