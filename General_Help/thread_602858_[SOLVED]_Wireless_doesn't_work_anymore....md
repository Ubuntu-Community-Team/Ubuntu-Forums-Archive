---
title: "[SOLVED] Wireless doesn't work anymore..."
date: 2007-11-04
forum: General Help
---

### Post by geek_Man on 2007-11-04
Hey all, since upgrading to Gutsy, my wireless has ceased to work. When I open nm-applet or something it doesn't even show me that wireless is an option. If someone could give me a step-by-step to get it fixed that would be great. If it helps, my wireless worked fine in Feisty. Thanks in advance!

P.S. Sorry if this has already been posted about...

---

### Post by Pumalite on 2007-11-04
I'm not much of a wireless guy, but I have a collection of links that might help you:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by geek_Man on 2007-11-05
Mmm... I don't think I saw anythig...

---

### Post by Tethylis on 2007-11-05
in the teminal type lspci and tell us what wireless card you have so that we are better able to help.

---

### Post by geek_Man on 2007-12-18
Okay, here's what it says:

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I'm able to get it to work in the old kernel, but not the new one...

---

### Post by geek_Man on 2007-12-23
Hellooo...

---

### Post by geek_Man on 2008-03-09
'Kay, for the record, I finally did get my wireless to work. When I upgraded, it's possible that the Restricted repos weren't enabled, so some of the modules weren't installed. I believe the package is linux-restricted-modules-2.6.20-16-generic. Now my I got my wireless. Happy, happy.

---

