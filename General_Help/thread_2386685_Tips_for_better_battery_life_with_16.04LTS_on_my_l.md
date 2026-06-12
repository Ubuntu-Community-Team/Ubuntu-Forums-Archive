---
title: "Tips for better battery life with 16.04LTS on my laptop?"
date: 2018-03-08
forum: General Help
---

### Post by bistwo on 2018-03-08
I have a Lenovo Thinkpad T450s (i5 5300u, 8GB DDR3, 512GB SSD, Intel HD 5500) and under Windows 10 in "power saver" mode, it can get nearly 10 hours of battery life, however on Ubuntu the max is around 3-4 hours.  Is there a tool I can install to get to manage the CPU and GPU power settings?  I have tried TLP but lscpu | grep MHz still shows the CPU running at full speed with boost enabled.

---

### Post by thehipho on 2018-03-08
There's a tool for system power consumption called powertop it could also adjust some power settings.

```
sudo apt-get install powertop
```

---

### Post by cruzer001 on 2018-03-08
Check these links out.

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

[https://wiki.archlinux.org/index.php/TLP](https://wiki.archlinux.org/index.php/TLP)

[https://www.phoronix.com/scan.php?page=article&item=ubuntu2017-tlp-powertop&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu2017-tlp-powertop&num=1)

---

