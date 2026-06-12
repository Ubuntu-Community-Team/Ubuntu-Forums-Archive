---
title: "What are the rules in ubuntu with drivers?"
date: 2008-03-08
forum: General Help
---

### Post by darkworld on 2008-03-08
I loaded my graphics driver like this

> sudo sh ./NVIDIA-Linux-x86_64-169.04-pkg1.run

If I want to load a different driver do I have to remove this one first or does another driver install just take priority?

If I have to remove first what is the way to do this?

---

### Post by julian67 on 2008-03-08
> **darkworld said:**
> I loaded my graphics driver like this



If I want to load a different driver do I have to remove this one first or does another driver install just take priority?

If I have to remove first what is the way to do this?

the different driver is for the same card or another nvidia card? are you changing it for an ATI card or are you just wanting to update the nvidia driver, or are you wanting to remove the proprietary driver and use the free one? You need to give some detail because each case will be different.

---

### Post by darkworld on 2008-03-08
im running the beta nvidia driver but i would like to change to the stable one.

./NVIDIA-Linux-x86_64-169.04

to

./NVIDIA-Linux-x86_64-169.12

keeping same graphics card.

---

### Post by julian67 on 2008-03-08
It should be pretty easy. You need to uninstall the old driver first. It's a lot like the install, you need to boot into terminal and again run the old installer but this time with --uninstall option, so you would run ```
sh your_beta_installer.run --uninstall
``` and then you can run the new driver installer ```
sh your_stable_installer.run
```

---

