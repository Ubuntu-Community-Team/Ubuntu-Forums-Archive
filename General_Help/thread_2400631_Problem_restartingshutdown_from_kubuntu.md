---
title: "Problem restarting/shutdown from kubuntu"
date: 2018-09-08
forum: General Help
---

### Post by jorritTyb on 2018-09-08
Hi all, firt a bit of explanation. I just got a new MSI gaming laptop (model GV72 8RE). There is a 256GB SSD for Windows 10 and I installed a new 512GB SSD for Kubuntu. On that I installed Kubuntu 18.04 (edited) and it works perfectly fine (I'm using it right now). However I have one issue. When I shut down or restart from ubuntu the laptop hard locksup and I have to hold down the power button to get out of that. This happens every time and it even happened the very first time right after installing kubuntu.

Any ideas how to solve this?

Another question. Is it possible (reliable) to use standby/sleep from kubuntu? i.e. like in windows, just close the lid and return later.

Thanks in advance!

---

### Post by TheFu on 2018-09-09
18.10 isn't released.  Need to ask all questions about in the "Development Release" subforum, not general help.

---

### Post by jorritTyb on 2018-09-09
> **wildmanne39 said:**
> *Thread moved to **Ubuntu Development Version for a more appropriate fit**.*

Actually sorry. I was wrong (it is so hard to find the version of ubuntu from within ubuntu itself). It is 18.04 (LTS) that I have installed.Sorry for the confusion

---

### Post by TheFu on 2018-09-09
Very easy.
```
$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.5 LTS"
```

or if you prefer a command:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:        16.04
Codename:       xenial

```

As for solving boot issues, I would check 2 things.
a) the boot log - **journalctl -b**
b) all the pre-boot stuff - BIOS settings and the output from a **boot-info** script.  This will show the layout of the connected HDDs, grub settings, where grub is installed and how it expects to be booted - BIOS or UEFI.  It will upload the data to a random webpage.  Just post the URL here.

---

