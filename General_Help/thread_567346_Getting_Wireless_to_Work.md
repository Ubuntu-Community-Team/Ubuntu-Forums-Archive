---
title: "Getting Wireless to Work"
date: 2007-10-04
forum: General Help
---

### Post by Naatan on 2007-10-04
Hi, having a bit of trouble getting wireless working on 7.10

I installed ndiswrapper so that I could use the windows drivers, however I think the old drivers are mixed up with the new ones now (the old ones didnt work)

When I do ndiswrapper -l I get the following:

```
$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4319) present (alternate driver: bcm43xx)
```

bcm43xx is the old driver.

When I do sudo dmesg I get the following error a lot of times:

```
[   50.188000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

Which is the old driver again.

Can anyone tell me how to get this sorted?

I got it working this way on Ubuntu 7.04 but then it didnt automatically install a (wrong) driver..

---

### Post by Naatan on 2007-10-04
hurray, installed restricted drivers and it worked :)

---

