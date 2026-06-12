---
title: "/boot file is full and must be cleared"
date: 2015-04-19
forum: General Help
---

### Post by okkie2 on 2015-04-19
I got this notification for the first time ever and do not know what it actually means . I obviously have to clear it but need guidance. Computer is up to date and a 1T hard 
drive about 5% used.
any help would be appreciated
Thanks

---

### Post by dino99 on 2015-04-19
with a standard installation, such issue is never met
[https://help.ubuntu.com/community/Baobab](https://help.ubuntu.com/community/Baobab)

---

### Post by Elfy on 2015-04-19
Does the warning say /boot file or folder? 

I bet LVM and a /boot partition of ~250Mb

Try removing old kernels.

This will do that, but also anything else that apt thinks you no longer need.

```
sudo apt-get autoremove
```

Alternatively use synaptic to search for and remove the old kernels.

---

### Post by okkie2 on 2015-04-22
Thanks Elfy problem solved

---

### Post by Elfy on 2015-04-22
> **okkie2 said:**
> Thanks Elfy problem solved

You need to keep an eye on that folder if this is the case.

---

