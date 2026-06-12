---
title: "how to run a sudo apt"
date: 2007-07-12
forum: General Help
---

### Post by francis.hammell on 2007-07-12
How do i run a sudo apt-get install -f

---

### Post by Espreon on 2007-07-12
Very simple enter it in a terminal and hit enter, simple as that!

---

### Post by francis.hammell on 2007-07-12
it asks for a password ont he terminal but it won't let me type anything in

---

### Post by davidjmayo on 2007-07-12
sudo before a command makes it run with root (admin) priviledges.
The password asked for is the same as your login password. for security it won't show in the terminal or echo any * or whatever
Just type the password and hit enter.

---

### Post by McNils on 2007-07-12
It does. You cant see it.

---

### Post by francis.hammell on 2007-07-12
thanks but now it is saying
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and when i type the dpkg thing into the terminal it says

dpkg: requested operation requires superuser privilege

what now?

---

### Post by sisco311 on 2007-07-12
```
sudo dpkg --configure -a
```

---

### Post by francis.hammell on 2007-07-12
thankyou all but i still haven't fixed it i did quite a bit on my own but now it is saying 

Selecting previously deselected package libc6-dev.
(Reading database ... 150128 files and directories currently installed.)
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up libtool (1.5.22-4) ...
Setting up gnome-common (2.18.0-0ubuntu1) ...
Setting up glade-gnome (2.12.1-6ubuntu2) ...

Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
francis@Francis-desktop:~$ 

what now?

---

### Post by Nythain on 2007-07-12
sudo apt clean
sudo apt-get update
try again
any luck???

---

### Post by francis.hammell on 2007-07-12
!!! thanks a bunch you guys it is working fine now oh thankyou so much i dunno what i would have done without these forums

---

