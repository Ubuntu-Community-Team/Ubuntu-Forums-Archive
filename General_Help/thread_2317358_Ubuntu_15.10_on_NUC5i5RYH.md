---
title: "Ubuntu 15.10 on NUC5i5RYH"
date: 2016-03-15
forum: General Help
---

### Post by TicoJohn on 2016-03-15
I recently purchased a NUC5i5RYH to use mainly for home theater (Kodi). One of the issues I have discovered with the NUC is that it has a pretty new graphics chip (Intel HD 6000). I have been a Debian user for years but find that the regular releases of Debian do not support that chipset, at least not without a LOT of fiddling around. It is my understanding that the problem is the linux kernel and that a newer kernel, like 4.2, is needed to resolve the problem. And I believe that Ubuntu has that newer kernel. Can someone verify that?  Also, does anybody here have experience installing 15.10 on the NUC5i5RYH, or a similar model with the HD 6000 graphics? It would be nice to get some feedback.

One other thing. If I download Ubuntu MATE 15.10, just to verify functionality in the LIVE mode, and then decide to install to the HDD, does the Ubuntu MATE install give a full Ubuntu system? I presume so but just want to verify.

Thanks in advance.

---

### Post by sandyd on 2016-03-16
> **TicoJohn said:**
> I recently purchased a NUC5i5RYH to use mainly for home theater (Kodi). One of the issues I have discovered with the NUC is that it has a pretty new graphics chip (Intel HD 6000). I have been a Debian user for years but find that the regular releases of Debian do not support that chipset, at least not without a LOT of fiddling around. It is my understanding that the problem is the linux kernel and that a newer kernel, like 4.2, is needed to resolve the problem. And I believe that Ubuntu has that newer kernel. Can someone verify that?  Also, does anybody here have experience installing 15.10 on the NUC5i5RYH, or a similar model with the HD 6000 graphics? It would be nice to get some feedback.

One other thing. If I download Ubuntu MATE 15.10, just to verify functionality in the LIVE mode, and then decide to install to the HDD, does the Ubuntu MATE install give a full Ubuntu system? I presume so but just want to verify.

Thanks in advance.

Kernel 4.2 is indeed in Ubuntu Wily: [http://packages.ubuntu.com/search?suite=wily&section=all&arch=any&keywords=linux-image-4.2&searchon=names](http://packages.ubuntu.com/search?suite=wily&section=all&arch=any&keywords=linux-image-4.2&searchon=names)

All of the official Ubuntu distributions can install to HDD and come with software/etc chosen by the distribution.

---

### Post by gordintoronto on 2016-03-16
Ubuntu Mate is not Ubuntu; it uses the Mate desktop rather than Unity.

Any 15.10 version includes the 4.2 kernel. My Xubuntu 15.10 upgraded to 4.2.0-34 today.

---

