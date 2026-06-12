---
title: "radeon HD 3850 installing Problem ubuntu 12.04 lts 64bit"
date: 2014-04-16
forum: General Help
---

### Post by 5vlastkzn on 2014-04-16
Hello guys,
My MB x58a-ud7 Rev 2.0
My Video card radeon HD 3850 
fresh install ubuntu 12.04 LTS 64 bit
and allows installing Problem this driver
i have tried all ways over the internet 
1- downloading the driver from ATI website
install all depends from linux headers 
after installing it allows Black screen have Load from fans

2- using this tutrial 
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-proprietary-ati-catalyst-video-drivers-fglrx/129200#129200](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-proprietary-ati-catalyst-video-drivers-fglrx/129200#129200)

3- [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

4- [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

and all did not work 
what is the problem with ati driver with with the 12.04 lts
and every method i used i had reinstall the os

---

### Post by Mark Phelps on 2014-04-16
> what is the problem with ati driver with with the 12.04 lts

The problem is that unless you go back to the initial rollout of 12.04 (12.04.1), the newer rollouts are incompatible with the AMD restricted drivers for your card.

AMD dropped support for their HD 2x/3x/4x-series cards last summer and the newer X-server middleware that comes installed on 12.04.2 and newer will not work with the older restricted drivers, and there are no newer restricted drivers for those cards.

The default Radeon driver is installed by default and that's what you have to work with, now.

---

### Post by 5vlastkzn on 2014-04-16
i could not found the 12.04 catalyst driver and it's deleted from amd website seems or upgrade my hardware or stock in to windows :P

---

### Post by su:bhatta on 2014-04-16
Have a look here: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

Use that at your own risk !

---

