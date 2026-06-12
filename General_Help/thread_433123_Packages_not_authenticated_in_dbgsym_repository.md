---
title: "Packages not authenticated in dbgsym repository"
date: 2007-05-04
forum: General Help
---

### Post by clconway on 2007-05-04
apt is failing to authenticate packages from the dbgsym repository.

I have added a key for the repo, following [the directions here]("https://wiki.ubuntu.com/DebuggingProgramCrash") 

> $ tail -1 /etc/apt/sources.list
deb [http://people.ubuntu.com/~pitti/ddebs](http://people.ubuntu.com/~pitti/ddebs) feisty main universe


> $ sudo apt-key list
<...>
pub   1024D/5E0577F2 2000-06-04
uid                  Martin Pitt <martin@piware.de>
uid                  Martin Pitt <mpitt@debian.org>
uid                  Martin Pitt <martin.pitt@ubuntu.com>
uid                  Martin Pitt <martin.pitt@canonical.com>
sub   2048g/11D9AE4E 2000-06-04


> $ sudo apt-get install sound-juicer-dbgsym 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sound-juicer-dbgsym
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 116kB of archives.
After unpacking 287kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  sound-juicer-dbgsym
Install these packages without verification [y/N]? 
E: Some packages could not be authenticated


---

### Post by Theimon on 2007-05-05
I'm getting a time-out on the keyserver, but if you trust the software it's probably safe to install it, even though it's not authenticated.

---

