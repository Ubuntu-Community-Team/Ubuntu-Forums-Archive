---
title: "Cannot find wireless card on laptop (have tried lshw -C network)"
date: 2012-12-04
forum: General Help
---

### Post by Gusss on 2012-12-04
Cannot find wireless card on laptop. I have tried lshw -C network logged in as super user - it just goes "PCI (sysfs) " for a bit the "SCSI" the just goes back to root@ubuntu:~# .
thing is once the additional drivers thing found the card , installed the driver and everything was fine, until restarting then it lost it again. Since then I've had to use a dongle.
Laptop is an HP6000

---

### Post by Gusss on 2012-12-05
nada ?

---

### Post by steeldriver on 2012-12-05
That's strange - let's see what lspci has to say

```
lspci -vnn | grep -e '\[0200\]' -e '\[0280\]'
```Why are you doing it in the root shell though? (if you are in the recovery console perhaps it's because networking is not enabled yet?)

---

