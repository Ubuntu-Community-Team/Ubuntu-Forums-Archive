---
title: "black screen before login site"
date: 2015-12-04
forum: General Help
---

### Post by Rafal612 on 2015-12-04
Hello,
 I'm using the latest version of ubuntu on my laptop. I installed dirvers for my graphic card from [http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)  (first download). Then i restart my laptop. Now i have bleck screen before login site. Any soultions ?

---

### Post by grahammechanical on 2015-12-04
At the Grub boot menu select Advanced options for Ubuntu & in that sub-menu select recovery mode and at the recovery mode select Resume. If that gets you to a working desktop remove that video driver.

Go to System Settings>Software & Updates>Additional Drivers tab and allow the utility time to find some drivers from the internet and then select the open source video driver. Once you have Ubuntu loading successfully you can use Additional Drivers to install a proprietary video driver. There is more likelihood of getting a stable video driver from Additional Drivers than downloading one from a manufacturer's web site.

Regards.

---

### Post by Rafal612 on 2015-12-04
Resume give the same result - black screen :/

---

