---
title: "Are these old udev rules still needed?"
date: 2018-05-25
forum: General Help
---

### Post by rsteinmetz70112 on 2018-05-25
I have several machines that began life a decade or more ago and have been continuously upgraded in hardware and software they are currently running 16/04 LTS I plan on upgrading to 18.04.1 LTS after it becomes available. 
I've been working on a problem and noticed that there were some very old rules in /etc/udev/rules.d 

```
root@thelma:/etc/udev/rules.d# ls -ld *
-rw-r--r-- 1 root root 34568 Apr 10  2008 45-libmtp7.rules
-rw-r--r-- 1 root root   761 Apr 21  2009 70-persistent-cd.rules
-rw-r--r-- 1 root root   593 Aug 16  2014 70-persistent-net.rules
```

I'm pretty sure the 70-persistent-net.rules is no longer necessary since the default naming of netwrok interfaces has changes.
The date on the file probably coincides with my upgrade from 12.04 LTS to 14.04 LTS

I have some newer installs I can check but they are not at this site and I don't have remote access.

---

### Post by rsteinmetz70112 on 2018-05-26
I checked a couple of newer install and there file are not there. I can't imagine why they would still be needed.

---

