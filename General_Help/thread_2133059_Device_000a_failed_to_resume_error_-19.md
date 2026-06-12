---
title: "Device 00:0a failed to resume: error -19"
date: 2013-04-06
forum: General Help
---

### Post by erikfig on 2013-04-06
Hello All,

I'm new to Linux.

I installed Ubuntu 12.10 on my Lenovo T500 and whenever I'm taking the computer out of sleep mode, I see the error: **Device 00:0a failed to resume: error -19**

Does anybody know a fix for this?

---

### Post by Toz on 2013-04-06
Hello and welcome to the forums.

What device is 00:0a? Try this from a terminal window:
```
dmesg | grep "00:0a"
```

Also, I remember reading somewhere that the tpm_tis module can be problematic. If you unload the module first:
```
sudo rmmod tpm_tis
```
...then suspend, does it work?

---

### Post by erikfig on 2013-04-07
> **Toz said:**
> Hello and welcome to the forums.

What device is 00:0a? Try this from a terminal window:
```
dmesg | grep "00:0a"
```

Also, I remember reading somewhere that the tpm_tis module can be problematic. If you unload the module first:
```
sudo rmmod tpm_tis
```
...then suspend, does it work?

Will try that today and let you know, thanks.

---

