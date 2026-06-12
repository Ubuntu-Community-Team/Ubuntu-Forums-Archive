---
title: "E: Unable to locate package"
date: 2012-11-24
forum: General Help
---

### Post by mthwgrn on 2012-11-24
```
local@Home-ET1331:~$ sudo apt-get install compat-drivers
[sudo] password for local: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package compat-drivers

```

Everytime I use the apt-get command (even when using sudo) I get this error.  NOT just for compat-drivers, but for anything...


Any explanations?

---

### Post by The Cog on 2012-11-24
You need to do an update after installing, to get it to read the online package database:
```
sudo apt-get update
```
But I don't think there is a package called compat-drivers.

---

### Post by mthwgrn on 2012-11-25
> **The Cog said:**
> You need to do an update after installing, to get it to read the online package database:
```
sudo apt-get update
```But I don't think there is a package called compat-drivers.

Thank you, updating as we speak... Also, the compat-drivers was something I was trying to get a wireless adapter to work. Also working on that issue.

---

