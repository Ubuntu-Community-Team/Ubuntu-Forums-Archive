---
title: "Converting Ubuntu to Ubuntu Studio?"
date: 2008-05-14
forum: General Help
---

### Post by mark_lar on 2008-05-14
Hi,

I have a fresh install of Ubuntu 8.04 LTS on my system. Due to lack of DVDs, I couldn't burn the image of Ubuntu Studio to DVD - I only had CDs. Is it possible to convert Ubuntu to Ubuntu Studio? 

I've googled it but only found answers for upgrading 7.10. Nothing for 8.04. 

Any help appreciated

Mark

---

### Post by pointone on 2008-05-14
```
sudo apt-get install ubuntustudio-desktop
```

---

### Post by mark_lar on 2008-05-14
I love you! Thanks!!

---

### Post by Drunky on 2008-05-14
Installing the ubuntustudio-desktop is not a complete upgrade.

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy)

This will get you the complete upgrade to Ubuntu Studio 8.04 from a vanilla installation of Ubuntu 8.04 Hardy.  This includes all meta-packages, even the real-time kernel.

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

