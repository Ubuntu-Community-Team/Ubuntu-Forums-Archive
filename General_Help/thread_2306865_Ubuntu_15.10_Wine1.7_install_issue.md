---
title: "Ubuntu 15.10 Wine1.7 install issue"
date: 2015-12-19
forum: General Help
---

### Post by justin76 on 2015-12-19
Hello everyone! I just did a fresh install of Ubuntu 15.10 and was trying to install Wine1.7. It won't let me install the newest version though. Here is the log from what I did.


```

justin@justin-VPCCW17FX:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
justin@justin-VPCCW17FX:~$ sudo apt-get update
justin@justin-VPCCW17FX:~$ sudo apt-get install wine1.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.44-0ubuntu1)
E: Unable to correct problems, you have held broken packages.

```

---

