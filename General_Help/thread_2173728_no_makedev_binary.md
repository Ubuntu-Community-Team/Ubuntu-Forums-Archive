---
title: "no makedev binary"
date: 2013-09-11
forum: General Help
---

### Post by reggler on 2013-09-11
Hi,

I wouldike to use makedev, apt-get tells me that it is installed already but I can not find its binary anywhere. I thought of removing and reinstalling it but apt-get wouldn't let me as it would break some depencies. Any idea what I can do other than downloading and compiling from source?

```

# apt-get install makedev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
makedev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
root@laptop-ron:~# which makedev
root@laptop-ron:~# apt-get remove makedev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 apache2.2-common : Depends: procps
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
Thanks,
Ron

---

