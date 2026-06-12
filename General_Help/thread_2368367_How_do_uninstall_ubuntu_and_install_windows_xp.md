---
title: "How do uninstall ubuntu and install windows xp?"
date: 2017-08-10
forum: General Help
---

### Post by 1happymom on 2017-08-10
So in need of help. Im a noob at this computer stuff and i love ubuntu but my child cannot use it. So i need to reinstall my windows xp. Can someone please HELP!!!! T.I.A.

---

### Post by HermanAB on 2017-08-10
Basically, you need to overwrite the first part of the hard disk with zeroes, after which a Windows XP install disk will be able to format the now seemingly empty disk and install itself.

For example:
$ sudo dd if=/dev/zero of=/dev/sda bs=1M count=10 

However, a better alternative may be to install Virtualbox and make a WinXP virtual machine running on Linux.

---

### Post by mörgæs on 2017-08-10
If Ubuntu is too unfamiliar you could try Lubuntu. It will also give much better performance for a computer from the XP era.

---

### Post by Bucky Ball on 2017-08-10
> **mörgæs said:**
> If Ubuntu is too unfamiliar you could try Lubuntu. It will also give much better performance for a computer from the XP era.

+1. Absolutely. Xubuntu is my preference, also very lightweight and works well on older machines (within reason).

Your child will have MUCH less issue with Lubuntu or Xubuntu, particularly if they have come from XP. I'd say they're even easier than that. Take note, though: kids learn quick and yours may be all over it and teaching you in a week or two as both Xubuntu and Lubuntu are pretty straightforward. 

You can download the ISOs of both, create install media and 'Try X/Lubuntu', depending on which you're trying. Your child, and youself, can then have a test drive before committing to an install.

Good luck whichever way you go. ;)

---

### Post by oldos2er on 2017-08-10
XP is long out of support. If you'd like to install a lighter supported Ubuntu version e.g. Lu- or Xubuntu, we'd be glad to help with that. 

Thread closed.

---

