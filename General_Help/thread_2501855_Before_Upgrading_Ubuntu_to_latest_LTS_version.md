---
title: "Before Upgrading Ubuntu to latest LTS version"
date: 2024-10-23
forum: General Help
---

### Post by hemantparmarh on 2024-10-23
Hi,

I am primarily application developer and not an expert on Ubuntu. Our web apps are based on MEAN stack. We have been running our apps on VPS with Ubuntu 20.04 for last 3 years.


1. What do I need to check before upgrading the OS to Ubuntu 24.x LTS?
2. When does it become necessary to update or upgrade the Ubuntu version?

hemant

---

### Post by grahammechanical on 2024-10-23
Ubuntu Long Term Support (LTS) versions get 5 years support. Ubuntu 20.04 LTS reaches end of support April 2025. The next Long Term Support release is Ubuntu 22.04 and that reaches end of support April April 2027. After that there is Ubuntu 24.04 LTS which reaches end of support April 2029.

We can do an online upgrade from one LTS release to the next but we cannot by-past the next LTS to upgrade to the following LTS. You will not be able to upgrade to 24.04 without first upgrading to 22.04. 

It is my opinion that the scripts that perform the online upgrade are designed to upgrade the default Ubuntu operating system. Some applications will also be upgraded to newer versions but not all applications in the app store. Applications especially installed by the user may not get upgrades and may break.

In my opinion the desktop user interface should be reverted back to a default condition. Specialized apps should be removed. Any Personal Package Archives (PPA) should be disabled. Software installed through a PPA may not have been upgraded to work with the newer LTS version. You should check out if the software has been complied to run on the newer LTS.

Back up your data. Some of us are of the opinion that it is best to do a fresh install and in this way skip an LTS version.
 
Your employer needs to develop a corporate plan for transitioning the machines to supported versions of the OS. Or subscribe to Ubuntu Pro.

[https://ubuntu.com/pro](https://ubuntu.com/pro)

[https://ubuntu.com/pricing/pro](https://ubuntu.com/pricing/pro)

Or take out some other service agreement with Canonical, the sponsor of Ubuntu.

Regards

---

