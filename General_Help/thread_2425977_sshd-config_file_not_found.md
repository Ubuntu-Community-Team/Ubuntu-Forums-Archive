---
title: "sshd-config file not found"
date: 2019-09-03
forum: General Help
---

### Post by satimis on 2019-09-03
Hi all

Ubuntu 16.04

&#10219; apt policy openssh-server```

openssh-server:
  Installed: 1:7.2p2-4ubuntu2.8
  Candidate: 1:7.2p2-4ubuntu2.8
  Version table:
 *** 1:7.2p2-4ubuntu2.8 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:7.2p2-4 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

&#10219; apt policy openssh-client```

openssh-client:
  Installed: 1:7.2p2-4ubuntu2.8
  Candidate: 1:7.2p2-4ubuntu2.8
  Version table:
 *** 1:7.2p2-4ubuntu2.8 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:7.2p2-4 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

&#10219; which sshd-config
No output

&#10219; which sshd```

/usr/sbin/sshd

```
It is an execute file.  Please help.

Thanks in advance

Regards
satimis

---

### Post by deadflowr on 2019-09-03
sshd_config is in the /etc/ssh directory.

---

### Post by satimis on 2019-09-03
> **deadflowr said:**
> sshd_config is in the /etc/ssh directory.
I got it.  Thanks

Regards
satimis

---

