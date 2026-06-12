---
title: "Best way to install Ubunutu alongside several other microsoft operating systems"
date: 2018-10-02
forum: General Help
---

### Post by sammymalone on 2018-10-02
I have an older **Dell m1210** laptop that has a 120gb hard drive. I first installed **windows xp** on 1/3 partition then **windows 2000** on 1/3 partition. Then I went to install **Lubuntu** and afterwords I could not boot into Windows XP or 2000. What is the best way to install these 3 operating systems each using 1/3 of the hard drive? Should I install Lubuntu 1st?

---

### Post by yancek on 2018-10-02
Installing the latest windows version last then Linux as you did usually is best.  Are you able to boot Lubuntu?  Windows bootloaders are backwards compatible so you should have installed xp AFTER w2K.  The way you did it you will probably need to manually configure the windows bootloader. 

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by guiverc on 2018-10-02
From Lubuntu, can you see the other 'windows' systems on your disk?   A simple `sudo update-grub` would cause a rescan of operating systems, updating your grub menu, and with luck will provide the option of the three when grub starts next time. It'd be the first thing I'd try

---

### Post by HermanAB on 2018-10-03
The best way?  Linux has the best scheduler.  Therefore install Linux and Virtualbox.  Then make as many Windows, BSD and other virtual machines as you need.  You can then run Windows in a window, the way the computer gods intended.

---

