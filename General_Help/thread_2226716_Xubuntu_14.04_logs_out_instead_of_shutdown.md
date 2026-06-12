---
title: "Xubuntu 14.04 logs out instead of shutdown"
date: 2014-05-28
forum: General Help
---

### Post by frank18 on 2014-05-28
Hi guys : i've been having this shutdown issue,every time i click in the icon in the corner to shutdown it presents me with 4 solutions,log out, Restart,shutdown,suspend,i click on shutdown and it goes to logout menu, it seems it only happens on my Dell P4 32Bit, i have a Lenovo I5 Intel desktop with the same Xubuntu 14.04 except 64bit  and it doesn't do that,
can you tell me what's the problem?

frank@frank-DIM4500:~$ apt-cache policy xfce4-power-manager
xfce4-power-manager:
  Installed: 1.2.0-3ubuntu4
  Candidate: 1.2.0-3ubuntu4
  Version table:
 *** 1.2.0-3ubuntu4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status
frank@frank-DIM4500:~$

---

### Post by slickymaster on 2014-05-29
The last version of the xfce4-power-manager is 1.2.0-3ubuntu5 ([https://launchpad.net/ubuntu/+source/xfce4-power-manager](https://launchpad.net/ubuntu/+source/xfce4-power-manager)) which brought several fixes to several issues. Can you please update your package and check if the problem subsist.

---

### Post by frank18 on 2014-05-30
> **slickymaster said:**
> The last version of the xfce4-power-manager is 1.2.0-3ubuntu5 ([https://launchpad.net/ubuntu/+source/xfce4-power-manager](https://launchpad.net/ubuntu/+source/xfce4-power-manager)) which brought several fixes to several issues. Can you please update your package and check if the problem subsist.

Thanks slickymaster, can you be more detailed on how i do that! thanks.

---

### Post by slickymaster on 2014-05-30
The xfce4-power-manager 1.2.0-3ubuntu5 was upload into Trusty on 2014-05-27, so if you run ```
sudo apt-get update && sudo apt-get upgrade
```should be enough to install it.

---

