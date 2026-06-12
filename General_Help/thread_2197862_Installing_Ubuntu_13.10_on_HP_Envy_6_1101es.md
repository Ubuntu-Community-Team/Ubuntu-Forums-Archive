---
title: "Installing Ubuntu 13.10 on HP Envy 6 1101es"
date: 2014-01-05
forum: General Help
---

### Post by ivan-balseiro91 on 2014-01-05
I have been quite a long time trying to install Ubuntu 13.10 on my Envy 6 1101es but the problem is the default AMD drivers provided by the OS drain and overheat my laptop really badly, its impossible to work on it like that, so I try to install the privative AMD driver from the GUI and when I restart I get a black screen with an X and nothing else loads, I would like to know if someone out there would be glad to help me solve this issue I have never been able to solve and I would like to so much.

What I think it really does is that when I install the drivers and restart the OS it breaks my GUI but I´m not possible to get that fixed, the only solution I have is to reinstall over and over again the OS and try other different ways of installing the driver but today my patience has ended and I would like to seek for some help to get this issue solved and be able to use my laptop with Ubuntu.

Thank you all and happy new year.

---

### Post by cariboo on 2014-01-05
Please don't create multiple threads on the same subject, I have merged your 3 threads.

---

### Post by ivan-balseiro91 on 2014-01-05
I didn´t know where I had to put it.

---

### Post by ivan-balseiro91 on 2014-01-05
I followed the guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)     no success at all.

---

### Post by ivan-balseiro91 on 2014-01-05
This doesnt work either, it says they dont exist... [https://wiki.ubuntu.com/X/Config/HybridGraphics#A13.10-1](https://wiki.ubuntu.com/X/Config/HybridGraphics#A13.10-1)

---

### Post by cariboo on 2014-01-05
I might help if you let us know what chipset/version your system uses.

---

### Post by ivan-balseiro91 on 2014-01-05
[COLOR=#333333][FONT=Ubuntu Beta]Installed [/FONT][/COLOR]fglrx[COLOR=#333333][FONT=Ubuntu Beta] and [/FONT][/COLOR]fglrx-pxpress, working perfect now.

---

### Post by ivan-balseiro91 on 2014-01-05
It is a Hybrid graphics 7670M with intel HD 3000, everything working fine now, thank you.

---

### Post by ivan-balseiro91 on 2014-01-06
For AMD/Intel Hybrid systems, run this command in the terminal :


sudo apt-get install fglrx fglrx-pxpress

---

