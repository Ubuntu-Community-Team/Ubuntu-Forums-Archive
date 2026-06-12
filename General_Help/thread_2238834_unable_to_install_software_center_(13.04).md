---
title: "unable to install software center (13.04)"
date: 2014-08-10
forum: General Help
---

### Post by planarian on 2014-08-10
Hi, I just yesterday resurrected a Linux install I hadn't used for a  year or two, and immediately found I was having problems with the  software center. I uninstalled it, but when I attempt to reinstall  (after running apt-get update) I end up with   ```
Err http://us.archive.ubuntu.com/ubuntu/ raring/main software-center all 5.6.0-0ubuntu2   404  Not Found [IP: 91.189.91.15 80] Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.6.0-0ubuntu2_all.deb  404  Not Found [IP: 91.189.91.15 80] E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```  I assume something has changed in the repository system, but I don't know where to get further information.

---

### Post by Dennis N on 2014-08-10
13.04 repositories are closed because that release is no longer supported. It's recommended that you upgrade to 14.04 release.

---

### Post by coffeecat on 2014-08-10
That's because 13.04 passed end-of-life in January. You need to re-install with 14.04, the current LTS (Long term support) version, which has three years' support (from April 2014) for Xubuntu and five years for Ubuntu. The intermediate releases that follow - 14.10, 15.04, 15.10 will be supported for 9 months only and then the next LTS will probably be 16.04.

---

### Post by planarian on 2014-08-10
Argh, I hate to hear that. Thanks.

---

