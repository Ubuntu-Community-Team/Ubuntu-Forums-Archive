---
title: "Have a good alternative for Modem manager GUI ?"
date: 2021-11-11
forum: General Help
---

### Post by aug7744 on 2021-11-11
Unhappily Modem Manger GUI has 2 issues :
- need remove the MODEM for read new SMS.
- SMS not are sorted by date hour.

Thanks for your reply.

---

### Post by ActionParsnip on 2021-11-11
What is the output of:
```

lsb_release -a
uname -a
apt-cache policy modem-manager-gui

```
Thanks

---

### Post by aug7744 on 2021-11-11
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal


---

Linux A1 5.11.0-27-generic #29~20.04.1-Ubuntu SMP Wed Aug 11 15:58:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

----

modem-manager-gui:
  Installed: 0.0.19.1-2
  Candidate: 0.0.19.1-2
  Version
 *** 0.0.19.1-2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        100 /var/lib/dpkg/status

---

