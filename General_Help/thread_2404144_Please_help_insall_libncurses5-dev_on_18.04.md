---
title: "Please help insall libncurses5-dev on 18.04"
date: 2018-10-20
forum: General Help
---

### Post by k.s.v. on 2018-10-20
I am trying to install libncurses5-dev on 18.04 and get the following:

```
$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libncurses5-dev : Depends: libtinfo5 (= 6.1-1ubuntu1) but 6.1-1ubuntu1.18.04 is to be installed
                   Depends: libncurses5 (= 6.1-1ubuntu1) but 6.1-1ubuntu1.18.04 is to be installed
                   Depends: libtinfo-dev (= 6.1-1ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

$ sudo apt-get install libtinfo-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libtinfo-dev : Depends: libtinfo5 (= 6.1-1ubuntu1) but 6.1-1ubuntu1.18.04 is to be installed
E: Unable to correct problems, you have held broken packages.



```

Will you please help me correct this?

I need that libncurses5-dev because it is required by Tizen studio  installer.

---

### Post by jeffpamplona on 2019-03-14
Exact same issue here.

---

### Post by mc4man on 2019-03-14
> **jeffpamplona said:**
> Exact same issue here.

open up Software & Updates > Updates tab > make sure security and updates repos are enabled. Refresh sources.

---

