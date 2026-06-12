---
title: "New install problems"
date: 2014-09-02
forum: General Help
---

### Post by PMDirac on 2014-09-02
I decided to do a clean install on a disk that I had partitioned to dual boot to 13.04 and windows 8 last year, but it seems that the installer failed to detect my previous swap space and preserve it during the reinstall. I am very disappointed that it is so difficult to configure swap in 14.04. 

Please tell me if I am misunderstanding, but it seems that this basic feature of linux is broken in the latest release in the sense that it is not set up correctly on install. 

Also, my devices were renamed such that what used to be /dev/sda5 mounted on / is now /dev/sda7, and what used to be /dev/sda7 is now /dev/sda6. At first I thought I had lost a TB of data (very scary), but that wasn't the case. Fortunately, this turned out to be a minor inconvenience.

---

### Post by obake2 on 2014-09-05
> **PMDirac said:**
> 
Please tell me if I am misunderstanding, but it seems that this basic feature of linux is broken in the latest release in the sense that it is not set up correctly on install. 



The bug for not detecting or configuring the swap properly only affects those who enabled Home Encryption. If there is no no encryption, Swap works as intended.

---

### Post by bapoumba on 2014-09-05
Thread moved to is own from [http://ubuntuforums.org/showthread.php?t=2224129](http://ubuntuforums.org/showthread.php?t=2224129).

---

