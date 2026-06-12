---
title: "i want to upgrade the kernel in a vps ubuntu 16.04"
date: 2019-06-29
forum: General Help
---

### Post by maxm4nu37 on 2019-06-29
i have a new vps server with ubuntu 16.04 at kayhosting with linux 2.6.32 and i cant install docker, i need to uppgrade  to a 3.1 kernel or high, i search some instructions online but i cant find the proper answer



hope you  guys can help me im very new on this.

---

### Post by CatKiller on 2019-06-30
That is very much not right. Ubuntu 16.04 came with the 4.4 kernel, upgradeable to 4.15 with the Hardware Enablement Stack. 2.6.32 was included with Ubuntu **10.04**, which hasn't been supported at all since 2015.

---

### Post by SeijiSensei on 2019-06-30
Some RedHat/CentOS versions like 6.10 use heavily patched kernels with 2.6.32 as the base. Sure you're running Ubuntu?

---

