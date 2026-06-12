---
title: "can't dist-upgrade linux 686"
date: 2007-02-08
forum: General Help
---

### Post by frogotronic on 2007-02-08
```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-headers-686 linux-image-686 linux-restricted-modules-686
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

what gives?

-------------------------------------------------------
*5 minutes later...*

The 2.6.15-28-686 versions of the ubuntu linux i686 kernel aren't in the repos yet and the dependencies can't be satisfied.

silly me.

---

### Post by toGoq on 2007-02-08
Yep, there is no linux 686 kernel for Edgy. There are only linux 368, and linux generic for other processors like 486,586,686,amdK7 or amdK8.
Work around: install linux 368 kernel for Dapper; run dist-upgrade again. After Edgy is installed properly, install linux generic kernel. Hope that help.

---

### Post by banditti on 2007-02-08
There is a very similar issue going on.  you might want to check out [http://ubuntuforums.org/showthread.php?t=356235&page=4](http://ubuntuforums.org/showthread.php?t=356235&page=4)

---

### Post by frogotronic on 2007-02-08
Hi,

  Well, I don't want to upgrade from 6.06.1 LTS to 6.10 (dapper to edgy).  I want to use Dapper Drake.

  I think its a reposository problem.

- CH

---

### Post by frogotronic on 2007-02-08
> **banditti said:**
> There is a very similar issue going on.  you might want to check out [http://ubuntuforums.org/showthread.php?t=356235&page=4](http://ubuntuforums.org/showthread.php?t=356235&page=4)

link is dead, please repost

---

### Post by banditti on 2007-02-08
[http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---

