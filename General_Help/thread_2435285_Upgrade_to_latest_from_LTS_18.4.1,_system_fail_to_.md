---
title: "Upgrade to latest from LTS 18.4.1, system fail to boot"
date: 2020-01-18
forum: General Help
---

### Post by area88 on 2020-01-18
Hi

My Ubuntu is 18.4.1 64 bits desktop version, after upgrade to latest, my system fail to boot with SMBus error. Please refer to attached screen capture for information
Is this a known issue in latest 18.4 LTS release?

[ATTACH=CONFIG]284820[/ATTACH]

System:
AMD® A8-7600 radeon r7, 10 compute cores 4c+6g × 4 
AMD® Kaveri
30.5 GiB neniery


Thanks

---

### Post by Impavidus on 2020-01-19
I don't know what causes that issue. To get a usable system, have you tried using the grub menu to boot an older kernel? Then we can investigate. Else you need a live disk. Can you tell us the packages involved in your latest upgrade? You can find it in the log files:```
grep " upgrade " /var/log/dpkg.log
```

---

