---
title: "No graphics after installed compat-drivers from source"
date: 2013-03-04
forum: General Help
---

### Post by wadelius on 2013-03-04
Hi dear forum,

I've been trying to get a new wireless adapter to work with ubuntu 12.10, and in that process I installed kernel 3.8 and compat-drivers 3.8 from source. I've written some about that in [http://ubuntuforums.org/showthread.php?t=2121020&page=4&p=12541242](http://ubuntuforums.org/showthread.php?t=2121020&page=4&p=12541242).

The 3.8 kernel worked fine, the problems started after I installed compat-drivers. The grapics wont work, not even switching to terminal. When I start the recovery root console and try to start X it crashes. 
```
cat /var/log/Xorg.0.log | grep EE
```
gives:
```
(EE) intel(0): failed to get resources: Invalid argument 
(EE) Screen(s) found, but none have a usable configuration.
 
 
...
 
 
Fatal server error: no screens found (EE)
```

```
 lspci | grep 945
```
gives:
```
...

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrate Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

...

```

I have never had to wrestle with graphics drivers on this level before, so I don't know what to do. Any suggestions would be welcome.

---

