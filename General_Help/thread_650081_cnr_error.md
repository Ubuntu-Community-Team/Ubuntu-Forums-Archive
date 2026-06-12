---
title: "cnr error"
date: 2007-12-25
forum: General Help
---

### Post by hyatt69 on 2007-12-25
i downloaded cnr for ubuntu 7.10 and the package installer comes up and says error:dependency is not satisfiable:libapt-pkg-status-libc6.6-6-4.5?
im very new with linux

---

### Post by S3Indiana on 2007-12-26
> **hyatt69 said:**
> i downloaded cnr for ubuntu 7.10 and the package installer comes up and says error:dependency is not satisfiable:libapt-pkg-status-libc6.6-6-4.5?
im very new with linuxFrom [here]("http://community.cnr.com/docs/DOC-1035"):```
# Uncomment the following two lines to add software from the 'backports' repository
deb     http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```

---

