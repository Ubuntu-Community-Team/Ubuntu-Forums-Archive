---
title: "dpkg --configure -a Error When Updating"
date: 2008-05-06
forum: General Help
---

### Post by GameBox 47 on 2008-05-06
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

When I try to update I get that error.  Anyone know what to do?  I'm a Ubuntu n00b.

---

### Post by tamoneya on 2008-05-06
go into terminal and run ```
sudo dpkg --configure -a
```

---

### Post by GameBox 47 on 2008-05-06
Everything was reconfigured fine, but on Evolution I get this...

```
Setting up evolution-data-server (2.22.1-0ubuntu2.1) ...
dpkg: error processing evolution (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 evolution

```

---

### Post by tamoneya on 2008-05-06
so reinstall evolution with this```
sudo apt-get remove evolution && sudo apt-get install evolution
```

---

### Post by rated_emman on 2008-06-05
HI! i got the same problem.... after i did it, i installed some updates and there was an error... i tried running the dpkg config again and i get this error:


Code: 

emmanuel@emmanuel-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-06-0ubuntu1); however:
  Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin

anybody? thank you!

---

### Post by Kevbert on 2008-06-05
In terminal
```
sudo apt-get install -f
```
should repair any damaged packages.

---

