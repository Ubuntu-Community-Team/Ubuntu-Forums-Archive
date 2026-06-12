---
title: "32-bit compatibility libs on Quantal"
date: 2012-10-30
forum: General Help
---

### Post by jaybee99 on 2012-10-30
Hi, I am affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294)

That is, I want to install the 32-bit compatibility libraries on a fresh Quantal, but here's what I find:

[HTML]$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch but it is not installable
E: Unable to correct problems, you have held broken packages.[/HTML]

What are my options, apart from waiting for some to fix this?

Ta

---

