---
title: "dpkg-reconfigure does not work"
date: 2004-12-01
forum: General Help
---

### Post by samgnu on 2004-12-01
I have just installed Warty 4.1 on an Asrock k7s8X motherboard with SIS chipset. It has no onboard video but I have ATI Radeon card. The installer incorrectly detemined the video card as SIS and not ATI. It failed to load the xserver but droped me back to the console. I then ran dpkg-reconfigure xserver-xfree86 and altered the driver to ATI. Everything worked perfectly including smooth accelerated graphics. However when I decided to alter the resolution and ran dpkg-reconfigure xserver-xfree86 again it does not get to the monitor section or resolution section. I get put into the console after accepting the prompt to write the DRI files to the config file. As I am considering a larger monitor how can I input different monitor specs.

---

### Post by az on 2004-12-01
sudo dpkg-reconfigure -plow whateverpackage

---

### Post by samgnu on 2004-12-02
No that did not work either. However I tried dpkg-reconfigure debconf accepted all defaults and then dpkg-reconfigure xserver-xfree86. and now its fine. 

Cheers, Samgnu

---

