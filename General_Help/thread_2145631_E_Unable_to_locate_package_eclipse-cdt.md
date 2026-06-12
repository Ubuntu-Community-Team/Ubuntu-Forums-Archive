---
title: "E: Unable to locate package eclipse-cdt"
date: 2013-05-16
forum: General Help
---

### Post by ReqValor on 2013-05-16
Hi,
I`ve tried to install eclipse-cdt through "sudo apt-get install eclipse-cdt". However I keep on getting the message "E: Unable to locate package eclipse-cdt", how do I get to install eclipse at ubuntu 13.04?

---

### Post by Reggy on 2013-05-16
Thats weird, 'eclipse-cdt' does exist in raring repos. [http://packages.ubuntu.com/raring/eclipse-cdt](http://packages.ubuntu.com/raring/eclipse-cdt)  Are you able to install any other software via apt-get?  Maybe the package list is not fetched, try 'sudo apt-get update' & 'sudo apt-get upgrade', before installing other software.

---

### Post by IT Researcher on 2013-05-17
> **Reggy said:**
> Thats weird, 'eclipse-cdt' does exist in raring repos. [http://packages.ubuntu.com/raring/eclipse-cdt](http://packages.ubuntu.com/raring/eclipse-cdt)  Are you able to install any other software via apt-get?  Maybe the package list is not fetched, try 'sudo apt-get update' & 'sudo apt-get upgrade', before installing other software.

same case here when i tried 'sudo apt-get update ' got output
Reading package lists... Done

and with 'sudo apt-get upgrade' got the output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


so what do i do now

---

