---
title: "Can't install  OS updates"
date: 2017-07-20
forum: General Help
---

### Post by Bob_Dennis on 2017-07-20
Ubuntu 16.04.2 LTS, supposedly low-latency.

I tried first to install updates from the Software update tab, it failed (I don't remember the error message, but I do remember something about it being a known error.)  I waited a few days in case the error was corrected,  and tried again, but the update just hung, no error message.  

'sudo apt-get update' produced no errors.

'sudo apt-get dist-upgrade' produced  just 
```
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

The suggested dpkg command produced a long stream of which I think these are the relevant bits:

```
...
dpkg: dependency problems prevent configuration of linux-image-lowlatency:
 linux-image-lowlatency depends on linux-image-4.4.0-83-lowlatency; however:
  Package linux-image-4.4.0-83-lowlatency is not installed.


dpkg: error processing package linux-image-lowlatency (--configure):
 dependency problems - leaving unconfigured

...



dpkg: dependency problems prevent configuration of linux-lowlatency:
 linux-lowlatency depends on linux-image-lowlatency (= 4.4.0.83.89); however:
  Package linux-image-lowlatency is not configured yet.


dpkg: error processing package linux-lowlatency (--configure):
 dependency problems - leaving unconfigured
...

dpkg: error processing package apport (--configure): package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
...
Errors were encountered while processing:
 linux-image-lowlatency
 linux-lowlatency
 apport






```

I also tried removing apport as follows:
 ```
 
sudo dpkg --remove --force-remove-reinstreq apport


dpkg: dependency problems prevent removal of apport:
 apport-gtk depends on apport (>= 0.41).


dpkg: error processing package apport (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 apport

```




What is my next move?

---

### Post by deadflowr on 2017-07-20
What happens if you first try to reinstall apport
```
sudo apt-get install --reinstall apport
```
and then try running the fix broken packages command
```
sudo apt-get install -f
```
?
Post back any results.

---

### Post by Bob_Dennis on 2017-07-20
Fixed!  
```

apt-get autoclean
apt-get update
apt-get upgrade
apt-get install -f
apt-get dist-upgrade
apt autoremove

```

Found from suggestions in other posts,  Thanks, forum!

---

