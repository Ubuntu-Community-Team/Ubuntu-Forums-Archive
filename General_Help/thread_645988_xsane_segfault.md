---
title: "xsane segfault"
date: 2007-12-20
forum: General Help
---

### Post by ronacc on 2007-12-20
When I try to start xsane to scan an image it segfaults and coredumps after a few seconds , either during or immeadiately after detecting scanners. I am using 7.04 fiesty fawn , the scanner is not the problem it works with a suse install on the same box. Xsane was working the last time I used it so an update must have nuked it but I have no idea which one since I dont use the scanner very often. the crash report in /var/crash/ dosent give any indication that I can see as to why it crashed , I reinstalled all sane and xsane packages no help . any Ideas on how to procede ?

---

### Post by geraldm on 2007-12-20
On a crash, in all probability an upgrade to try the latest version would be recommended to see if the problem still persists.  I have seen no segfault corrections in the upgrade notes to xsane.
The latest version is xsane-0.995 dated Nov 21, 2007.  Also I would suggest mentioning the model of the scanner and the sane-backend that would have been used. Those may provide more clues for a similar problem.

Gerald

---

### Post by ronacc on 2007-12-20
the latest version I show in synaptic for fiesty (7.04) is 0.991  with software sources freshly updated and backports enabled.  as I said I reinstalled all sane and xsane packages , they         reinstalled normaly with no squawks about dependencies , the scanner is an epson perfection 1650 , it was working the last time I tried it . it does work with my suse install on the same box . I donot believe it is a scanner problem since xsane never gets that far . the scanner is correctly identfied and shown in harware info and lsusb . I may try getting xsane 0.995 as source and localy compiling and see what happens.

---

