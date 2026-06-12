---
title: "Xserver help"
date: 2007-09-22
forum: General Help
---

### Post by Imsati on 2007-09-22
I recently acquired a new MoBo. My XP Drive works great, but Ubuntu 7.04 and Kubuntu 6.06 would not load up correctly afterwards. I tried some recommendations to reconfigure the Xserver, but nothing worked. So I tried to reinstall both today and am now having major problems.

Kubuntu 6.06 will install via the Alt CD, but is not able to configure the network, then upon a successful install, it will not load (it will look like it is, then freeze).

Ubuntu 7.04 will start to load, then show the xserver error and freeze completely.

Any ideas? Using the Alt CD, I erased every partition on the Linux drive during the setup stage and created new ones to wipe every trace of old programming off the drive.

It is possible to get my old MoBo back, but it's already in another computer so it will take some time and effort.

--Jay

---

### Post by Imsati on 2007-09-22
So after some testing, I isolated it to my video card (Nvidia GS 7100). I took the card out, hooked the monitor to the on-board port and Ubuntu 7.04 loaded up.

Can I install using that method and then  install the card afterwards and hope for the best or is there another way?

I also copied down the error report I was getting:

(EE) Screens found, but none have a usable configuration.
(Then about 2 lines below that...)
Fatal server error:
   no screens found


Not sure if anything can be determined from those, but figured I'd post it.

--Jay

---

### Post by Imsati on 2007-09-22
Also forgot to mention that my video card is a PCIE x61 and my MoBo is only capable of x4. Will that have anything to do with it? XP works fine--oh well.

Took the card out again and loaded into Kubuntu 6.06 no problem.

---

