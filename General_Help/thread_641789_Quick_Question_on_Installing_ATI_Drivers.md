---
title: "Quick Question on Installing ATI Drivers"
date: 2007-12-15
forum: General Help
---

### Post by -=BINGO-BANGO=- on 2007-12-15
As im using [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=show&redirect=BinaryDriverHowto%2Fati#head-796aa4d6d0477c8ed722acef1878cc5626855ae3") to install ATI drivers it says "If it is does not already exist, then edit the line starting with DISABLED_MODULES so that fglrx is included in the list."

But wouldnt i NOT want it in the list of disabled modules if it is the type of driver that i am using?

---

### Post by jessika-kaos on 2007-12-15
No, that's right. See here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

> Blacklist old fglrx module from linux-restricted-modules:

As Ubuntu Gutsy's linux-restricted-modules package includes the fglrx module from an old driver version (8.37.6), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead. 

---

