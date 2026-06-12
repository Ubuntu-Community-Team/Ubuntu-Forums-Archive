---
title: "Ubuntu 18.04 network driver"
date: 2024-09-11
forum: General Help
---

### Post by allentony007 on 2024-09-11
How do I install Network Driver on hp pro mini running Ubuntu 18.04?

---

### Post by coffeecat on 2024-09-11
Support not chat. *Thread moved to **General Help**.*

---

### Post by guiverc on 2024-09-11
You do know *community* support has ended for Ubuntu 18.04 LTS.  It was released in 2018-April (thus 18.04) with five years of standard support, which ended last year.

[https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/](https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/)

Support now is largely from Canonical, who provide ESM or Extended services.

---

### Post by yancek on 2024-09-11
Take a look at the Ubuntu site below to find which releases are still supported, what support you get and for what duration.  Might be a good idea to bookmark the site forfuture reference.  You've waited too long so now it will either be a very convoluted process of finding the archives for the old release and configuring the sources.list to update.  Much easier to back up your personal and maybe configuration files to another drive and install a newer version of Ubuntu which is supported.

 [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

---

### Post by grahammechanical on 2024-09-11
What network driver?  WiFi? Ethernet? USB?

Drivers in Linux come in a package call linux-firmware. Over time the Linux developers add drivers of new hardware and each new version of Ubuntu installs the latest linux-firmware package.

If your hardware is newer then Ubuntu 18.04 it is possible that 18.04 does not have Linux drivers for your hardware. Another reason for using newer versions of Ubuntu.

Regards

---

