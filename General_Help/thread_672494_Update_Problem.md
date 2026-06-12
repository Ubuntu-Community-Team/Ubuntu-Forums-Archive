---
title: "Update Problem"
date: 2008-01-19
forum: General Help
---

### Post by TheMixtureMedia on 2008-01-19
Hi there I have Ubuntu 7.10 x64 I try doing an update and it comes up with this problem 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I go into terminal to fix the problem and it ask me to go into super user and it will not take my password for super user. There is no other users on this system just me and I have no idea why it will not take my password. Can someone please help me with this problem please.

---

### Post by dan0z on 2008-01-19
Run: "sudo dpkg --configure - a"

It will then prompt for you password.

It should then run.

Dan

---

### Post by TheMixtureMedia on 2008-01-19
It comes up with a error

dpkg: error processing a (--configure):
 no package named `a' is installed, cannot configure
Errors were encountered while processing:
 a


Please help anyone :-(

---

### Post by oldos2er on 2008-01-19
Should be "sudo dpkg --configure -a"

---

### Post by TheMixtureMedia on 2008-01-19
Got it to work thank you.

---

