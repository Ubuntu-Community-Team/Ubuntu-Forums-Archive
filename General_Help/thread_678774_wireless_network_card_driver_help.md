---
title: "wireless network card driver help"
date: 2008-01-26
forum: General Help
---

### Post by flyinsqrl on 2008-01-26
ok i have a belkin wireless card and i have the driver disc but how do i install the driver on ubuntu? thanks for the help guys ;)

---

### Post by flyinsqrl on 2008-01-26
a friend of mine said i need to program my own driver, but i'm new to linux, help would be much appreciated

---

### Post by hahahan on 2008-01-26
Flyingsqrl,

Have a look here :[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShooting](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShooting)

---

### Post by flyinsqrl on 2008-01-26
that doesn't help me much but thanks for the help ;)

---

### Post by flyinsqrl on 2008-01-26
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

I have the f5d7000 please help

---

### Post by danwood76 on 2008-01-26
Which version?

It looks like that card uses 3 different chipsets, all three have native linux drivers but if you cant get them to work you can use ndiswrapper to load the windows drivers (although its quite unstable using that method)

regards,
Danny

---

### Post by flyinsqrl on 2008-01-26
Belkin F5D700 wireless G card, that help at all, i already tried that method but its soo confusing and hard, thanks for the help and keep it up

---

### Post by flyinsqrl on 2008-01-26
ok i have the first chipset, i can't figure a way to get this card to work please help.

---

### Post by danwood76 on 2008-01-27
Can you check in the restricted drivers manager (System >  Administration > Restricted Drivers Manager) to see if the broadcom wifi drivers are listed?
If they are enable them and restart and the wiresless card should work.

If that doesnt work I found this thread that might help you:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

regards,
Danny

---

